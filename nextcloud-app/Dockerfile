FROM nextcloud:23.0.3-apache

# Install libpq-dev for PHP-Extension pgsql
# Install postgresql-client for Backup-App
RUN apt-get update \
    && apt-get install -y  \
      libpq-dev \
      postgresql-client \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*

# Package for Backup-App to be able to talk to Postgres via PHP
# See https://stackoverflow.com/questions/47603398/docker-php-with-pdo-pgsql-install-issue
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install pdo pdo_pgsql pgsql
