# INSTALL PHP 
````
yum install epel-release yum-utils -y

yum install http://rpms.remirepo.net/enterprise/remi-release-7.rpm

yum -y remove php*
````

## enable disable package control
````
yum-config-manager --enable remi-php70   [Install PHP 7.0]
yum-config-manager --enable remi-php71   [Install PHP 7.1]
yum-config-manager --enable remi-php72   [Install PHP 7.2]
yum-config-manager --enable remi-php73   [Install PHP 7.3]
````

## DISABLE PHP7.3
````
yum-config-manager --disable remi-php73
````

## DISABLE PHP5.4
````
yum-config-manager --disable remi-php54
````

## ENABLE PHP7.2
````
yum-config-manager --enable remi-php72
````

## install package php

````
yum -y install php php-cli php-fpm php-mysqlnd php-zip php-devel php-gd php-mcrypt php-mbstring php-curl php-xml php-pear php-bcmath php-json php-pgsql
yum install php-mysql php-mysqlnd -y
yum install  php-intl php-soap -y
````

## install composer
````
curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
composer -v
````

## config php
````
nano /etc/php-fpm.d/www.conf

nano /etc/php.ini
````

## check version php
````
php -v
````

## service control
````
systemctl status php-fpm.service

systemctl restart php-fpm.service

systemctl enable php-fpm.service
````

## install addon package

````
curl https://packages.microsoft.com/config/rhel/7/prod.repo > /etc/yum.repos.d/mssql-release.repo

yum remove unixODBC-utf16 unixODBC-utf16-devel -y 

yum install php-sqlsrv php-pdo_sqlsrv -y

(IF ERROR => yum --enablerepo=remi-safe -y install php72-php-sqlsrv php72-php-pdo_sqlsrv)
````


## To get the current memory_limit value, run:  shell 
````
php -r "echo ini_get('memory_limit').PHP_EOL;"

````

## Try increasing the limit in your php.ini file (ex. /etc/php5/cli/php.ini for Debian-like systems): Use -1 for unlimited or define an explicit value like 2G
````
memory_limit = -1
````

## To get loaded php.ini files location try: shell command
````
php --ini
````

## Another quick solution:
````
php composer.phar COMPOSER_MEMORY_LIMIT=-1 require hwi/oauth-bundle php-http/guzzle6-adapter php-http/httplug-bundle
````

## in php script 
````
ini_set("memory_limit","512M");
````
