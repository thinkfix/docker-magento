FROM php:7.1-fpm

RUN apt-get update
RUN apt-get install -y apt-transport-https \
                    libpcre3-dev \
                    libpq-dev \
                    libmemcached-dev \
                    libicu-dev \
                    zlib1g-dev \
                    libpng-dev \
                    libxslt-dev \
                    libzip-dev \
                    libjpeg-dev \
                    libfreetype6-dev \
                    libjpeg62-turbo-dev \
                    librabbitmq-dev

RUN pecl install xdebug-2.9.0 amqp

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/

RUN docker-php-ext-install opcache \
                           pdo_mysql \
                           pgsql \
                           pdo_pgsql \
                           intl \
                           gd \
                           bcmath \
                           xsl \
                           soap \
                           zip \
                           sockets

WORKDIR /var/www

RUN chmod -R 0777 /var/log

#CMD ["/usr/bin/supervisord"]
