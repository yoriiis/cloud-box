# cloud-box

Runs a suite of services for a full-fledged cloud using Compose. Uses a bunch of a community-built Docker images.

## Services

- [Nginx proxy](https://hub.docker.com/r/jwilder/nginx-proxy/dockerfile)
- [Nextcloud](https://hub.docker.com/_/nextcloud/)
- [Mariadb](https://hub.docker.com/_/mariadb)

## Getting started

### Prerequisite and dependencies

Install all dependencies list below on the server:

- [Nginx](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-18-04-quickstart)
- [Certbot](https://certbot.eff.org)
- [Docker & Docker Compose](https://www.digitalocean.com/community/tutorials/comment-installer-et-utiliser-docker-sur-ubuntu-18-04-fr)
- [GIT](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-18-04-quickstart)

### Clone the repository

Clone the repository on the server in the `home` directory.

### Change permissions

Change permissions of all service directories to add the group `docker`:

```
chown <user_name>:docker mariadb nextcloud
```

### Edit the .env file

By default `.env` file is not versioned, run the following command to duplicate `.env.dist` and fill the file:

```
cp .env.dist .env
```

Update corresponding variables:

- `RESTART_MODE` - Docker restart mode
- `TIME_ZONE` - Time zone of containers
- `HOST_NAME` - Domain attach to the server
- `MYSQL_DATABASE` - MySQL database name
- `MYSQL_USER` - MySQL user
- `MYSQL_PASSWORD` - MySQL password
- `MYSQL_ROOT_PASSWORD` - MySQL root password

Like the following example:

```
RESTART_MODE=unless-stopped
TIME_ZONE=Europe/Paris
HOST_NAME=domain.com
MYSQL_DATABASE=nextcloud
MYSQL_USER=myuser
MYSQL_PASSWORD=mypassword
MYSQL_ROOT_PASSWORD=mysuperpassword
```

## Start the Docker Compose 🚀

Simply start all the services with the commands below, which uses the `docker-compose.yml` file by default.

```bash
# -d option let you run containers in the background
docker-compose up -d
```

## Licence 🤞

`cloud-box` is licensed under the [MIT License](http://opensource.org/licenses/MIT).

Created with ♥ by [@yoriiis](http://github.com/yoriiis).
