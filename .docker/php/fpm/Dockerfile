FROM php:8.1.4-fpm

RUN apt-get update && apt-get install -y unzip

# install-php-extensions
ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions && install-php-extensions mcrypt pdo_mysql xdebug
# /install-php-extensions

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --quiet

# Copy the files at the end of the image build
COPY php.ini /usr/local/etc/php/php.ini
COPY php-fpm.conf /usr/local/etc/php-fpm.d/zzz-docker.conf
COPY xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini
