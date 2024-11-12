# docker-php-mysql
A Docker container with Nginx, PHP, MySQL, phpMyAdmin, and SSL support.

## Usage

### Clone This Repository

From the Terminal, clone this repository to your local machine.
``` sh
git clone git@github.com:rootalley/docker-php-mysql.git
```
Change to the project root directory.
``` sh
cd docker-php-mysql
```

### Set Up SSL Certificates

Generate new self-signed certificate and key files.

> [!NOTE]  
> This repository includes `self-signed.crt` and `self-signed.key` files in its `nginx/certs` directory as placeholders. These placeholder files should be and will be overwritten by this operation.

``` sh
# From the project root directory
openssl req -new -newkey rsa:2048 -days 365 -nodes -x509 -keyout nginx/certs/self-signed.key -out nginx/certs/self-signed.crt
```
### Set Up Environment Variables
Use your favorite text editor to edit the `.env` file to specify your desired parameters.

### Install and Launch Docker

Download and install [Docker Desktop](https://www.docker.com/).

### Start Your Docker Container

Return to the project root directory and start the container.
``` sh
# From the project root directory
docker compose up -d
```

### Verify Everything's Working

Open your web browser and connect to [https://localhost](https://localhost). You should see a PHP information screen.

> [!NOTE]  
> You may see a security warning because the certificate in use is self-signed.

Connect to [http://localhost:8081](http://localhost:8081). You should see a phpMyAdmin login screen. (The default username is `root` and the default password is set to the value of `MYSQL_ROOT_PASSWORD` in the `.env` file.)

> [!NOTE]  
> This connection is HTTP (not HTTPS) because I haven't configured that yet!

### Shutting Down

Stop your Docker Container.
``` sh
# From the project root directory
docker compose down
```
