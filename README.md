# SETUP PHPMYADMIN

### ENV
```sh
_PHP_VERSION=8.4
```

### Install
- **Apache2**
    ```sh
    packages=(
        apache2
        libapache2-mod-php
        phpmyadmin
        util-linux
        php${_PHP_VERSION}-xml
        php${_PHP_VERSION}-mbstring
    )
    sudo apt install --no-install-suggests --no-install-recommends ${packages[@]}
    ```

- **Lighttpd**
    ```sh
    packages=(
        lighttpd
        phpmyadmin
        php${_PHP_VERSION}-cgi
        util-linux
    )
    sudo apt install --no-install-suggests --no-install-recommends ${packages[@]}
    ```

### Setup
```sh
sudo a2dismod mpm_event mpm_prefork php${_PHP_VERSION}
sudo a2enmod php${_PHP_VERSION}
sudo systemctl restart apache2.service
```

### Run
```sh
open localhost/phpmyadmin
```