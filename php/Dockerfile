#below is for docker file

#FROM php:alpine3.8
FROM php:7.3-fpm-alpine

# Version
ENV PHPREDIS_VERSION 4.0.1

# Timezone
#RUN /bin/cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
 #   && echo 'Asia/Shanghai' > /etc/timezone

# Libs
RUN apk add --update --no-cache curl  wget git zip autoconf gcc m4 make g++ openssl

ADD ./composer /usr/local/bin/composer
# Composer
RUN composer self-update --clean-backups && docker-php-ext-install pdo_mysql bcmath sockets 

# Redis extension
RUN wget http://pecl.php.net/get/redis-${PHPREDIS_VERSION}.tgz -O /tmp/redis.tar.tgz \
    && pecl install /tmp/redis.tar.tgz \
    && rm -rf /tmp/redis.tar.tgz \
    && docker-php-ext-enable redis

#ADD ./swoole /tmp/
#RUN cd /tmp &&  phpize && ./configure --enable-openssl \
#&& make && make install && docker-php-ext-enable swoole

#RUN pecl install swoole && docker-php-ext-enable swoole

