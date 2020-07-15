FROM drupal:8.9.1-fpm

RUN apt-get update && apt-get install -y \
    curl \
    git \
    vim \
    wget

ENV DRUSH_VERSION 10.3.1

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php && \
    mv composer.phar /usr/local/bin/composer  \
    && composer global require drush/drush:${DRUSH_VERSION} \
    && ln -s ~/.composer/vendor/drush/drush/drush /bin/drush \
    && php -r "unlink('composer-setup.php');"

WORKDIR /var/www

RUN composer global require zaporylie/composer-drupal-optimizations
RUN composer global require hirak/prestissimo
