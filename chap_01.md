I. Install nginx

1.  Install on ubuntu
    sudo apt-get update
    sudo apt install -y curl gnupg2 ca-certificates lsb-release debian-archive-keyring

            curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor | tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null

            OS=$(lsb_release -is | tr '[:upper:]' '[:lower:]')
            RELEASE=$(lsb_release -cs)
            echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] http://nginx.org/packages/${OS} ${RELEASE} nginx" | tee /etc/apt/sources.list.d/nginx.list

    apt-get update
    apt-get install -y nginx
    nginx

    On ubuntu, apache is default for web server an run on port 80. We need to change port default web server for nginx from 80 to 8080

    cd /etc/nginx/sites-available/
    sudo nano default

    -   update:
        listen 8080 default_server;
        listen [::]:8080 default_server;

2.  check status
    nginx -t

    2.1 sudo systemctl start nginx (start)
    2.2 sudo systemctl enable nginx (enable when os started)
    2.3 sudo systemctl status nginx (check status)
