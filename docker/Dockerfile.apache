FROM ubuntu:latest
MAINTAINER vlad

#Install updates and apache

RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noniteractive apt-get -y install apache2

#Installing openssl
RUN apt-get install openssl
RUN a2enmod ssl
#Setting Apache env variables
ENV TZ=Europe/Kyiv
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2

#Copying website repo 
ADD website /var/www/website

#Updating apache config
ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf

#Exposing 80 port
EXPOSE 80, 443

#Running web server
CMD /usr/sbin/apache2ctl -D FOREGROUND
