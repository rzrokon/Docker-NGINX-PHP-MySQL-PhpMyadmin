# Docker NGINX PHP MySQL PhpMyadmin

Easy PHP MySQL development with Docker and Docker Compose.

With this project you can quickly run the following:

- [NGINX](https://hub.docker.com/_/nginx)
- [PHP](https://hub.docker.com/_/php)
- [phpMyAdmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin/)
- [MySQL](https://hub.docker.com/_/mysql/)

Contents:

- [Requirements](#requirements)
- [Configuration](#configuration)
- [Installation](#installation)
- [Usage](#usage)

## Requirements

Make sure you have the latest versions of **Docker** and **Docker Compose** installed on your machine.

Clone this repository or copy the files from this repository into a new folder. In the **docker-compose.yml** file you may change the IP address (in case you run multiple containers) or the database from MySQL to MariaDB.

Make sure to [add your user to the `docker` group](https://docs.docker.com/install/linux/linux-postinstall/#manage-docker-as-a-non-root-user) when using Linux.

## Configuration

Edit the `.env` file to change the default IP address, MySQL root password and Database name.

## Installation

Open a terminal and `cd` to the folder in which `docker-compose.yml` is saved and run:

```
docker-compose up
```

This creates two new folders next to your `docker-compose.yml` file.

* `data` – used to store and restore database dumps and initial databse for import
* `web` – the location of your php application files

The containers are now built and running. You should be able to access the WordPress installation with the configured IP in the browser address. By default it is `http://127.0.0.1`.

For convenience you may add a new entry into your hosts file.

## Usage

### Starting containers

You can start the containers with the `up` command in daemon mode (by adding `-d` as an argument) or by using the `start` command:

```
docker-compose start
```

### Stopping containers

```
docker-compose stop
```

### Removing containers

To stop and remove all the containers use the`down` command:

```
docker-compose down
```

Use `-v` if you need to remove the database volume which is used to persist the database:

```
docker-compose down -v
```

### Project from existing source

Copy the `docker-compose.yml` file into a new directory. In the directory you create two folders:

* `data` – here you add the database dump or paste to init.sql
* `web` – here you copy your existing php project files

You can now use the `up` command:

```
docker-compose up
```

This will create the containers and populate the database with the given dump.


### Creating database dumps

```
./export.sh
```


### phpMyAdmin

You can also visit `http://127.0.0.1:8000` to access phpMyAdmin after starting the containers.

The default username is `root`, and the password is the same as supplied in the `.env` file.
