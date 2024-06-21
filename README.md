# docker-lamp

```
chomd +x install && ./install

# OR

docker compose up -d
docker exec -it app bash -c "/script/install-apache"
docker exec -it app bash -c "/script/install-php 7.3 dev"
docker exec -it app bash -c "/script/install-php 7.2 dev"
docker exec -it app bash -c "/script/install-php 5.6 dev"

docker compose stop -t 0 app
docker compose rm -f app
docker compose up -d app
docker compose logs app
docker ps
```

```
## Sample configuration file: 
# apache2/sites-enabled/hello-world.conf
<VirtualHost *:80>
  ServerAdmin  phamphu232@gmail.com
  ServerName   hello-world.local
  ServerAlias  foo.example.com bar.example.com others.example.com
  DocumentRoot /var/www/hello-world/public

  ErrorLog  /var/www/error_log
  CustomLog /var/www/access_log common

  <Directory "/var/www/hello-world/public">
    Options FollowSymLinks
    AllowOverride All
    Require all granted
    Allow from all
  </Directory>

  <FilesMatch \.php$>
    # For Apache version 2.4.10 and above, use SetHandler to run PHP as a fastCGI process server
    SetHandler "proxy:unix:/run/php/php7.3-fpm.sock|fcgi://localhost"
  </FilesMatch>
</VirtualHost>


## phpMyAdmin configuration options
# Download https://www.phpmyadmin.net/downloads/
# Copy and Edit /var/www/phpmyadmin/config.sample.inc.php 
Alias /phpmyadmin /var/www/phpmyadmin
```