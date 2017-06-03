# wysantos/glpi

# Docker Container GLPI
Criando a imagem online

cd src docker build -t wysantos/glpi .

# Utilização

## Iniciando o Container do DataBase:
```
docker run -d -t
-v $(pwd)/mysql:/var/lib/mysql
-e MYSQL_ROOT_PASSWORD=rootpass
-e MYSQL_DATABASE=glpidb
-e MYSQL_USER=glpi
-e MYSQL_PASSWORD=glpipass
-e SET_CONTAINER_TIMEZONE=true
-e CONTAINER_TIMEZONE=America/Sao_Paulo
--name glpi-db mariadb
```

## Iniciando o Container da Aplicação:
```
docker run -d -t
-p "80:80" -p "443:443"
--link glpi-db:glpi.db
-v $(pwd)/public_html/glpi:/var/www/html/glpi
-e SET_CONTAINER_TIMEZONE=true
-e CONTAINER_TIMEZONE=America/Sao_Paulo
--name glpi-app glpi
```
