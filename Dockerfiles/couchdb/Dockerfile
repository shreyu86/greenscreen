FROM ubuntu:14.04

# install couchdb from https://launchpad.net/~couchdb/+archive/ubuntu/stable
ENV COUCHDB_VERSION 1.6.1-0ubuntu2

RUN apt-get update -y \ 
    && DEBIAN_FRONTEND=noninteractive apt-get install -y software-properties-common \ 
    && DEBIAN_FRONTEND=noninteractive add-apt-repository -y ppa:couchdb/stable \ 
    && apt-get update -y \ 
    && DEBIAN_FRONTEND=noninteractive apt-get install -y couchdb=$COUCHDB_VERSION \ 
    && apt-get clean \ 
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

RUN echo "[couchdb]\
    \nuri_file = /tmp/couchdb.uri\
    \n\
    \n[httpd]\
    \nbind_address = 0.0.0.0\
    \nport = 5984" > /etc/couchdb/local.ini

VOLUME ["/var/log/couchdb", "/var/lib/couchdb", "/etc/couchdb"]

EXPOSE 5984

CMD ["couchdb"]


