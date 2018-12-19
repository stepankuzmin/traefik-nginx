# traefik-nginx

A simple [docker-compose](https://docs.docker.com/compose/) configuration for [traefik](https://traefik.io/) in front of nginx.

**Why?** Because traefik [doesn't support caching](https://github.com/containous/traefik/issues/878) currently.

## Usage

```shell
docker-compose up
```

```shell
curl -i -H "Host: localhost" "http://localhost:80"

HTTP/1.1 200 OK
Content-Length: 325
Content-Type: text/plain; charset=utf-8
Date: Wed, 19 Dec 2018 10:51:44 GMT
Server: nginx/1.15.5

Hostname: 8c187198484d
IP: 127.0.0.1
IP: 172.23.0.4
GET / HTTP/1.1
Host: front
User-Agent: curl/7.54.0
Accept: */*
Accept-Encoding: gzip
Connection: close
X-Forwarded-For: 172.23.0.1
X-Forwarded-Host: localhost
X-Forwarded-Port: 80
X-Forwarded-Proto: http
X-Forwarded-Server: e244ed1d0ae0
X-Real-Ip: 172.23.0.1
```

```shell
curl -i -H "Host: api.localhost" "http://localhost:80"

HTTP/1.1 200 OK
Content-Length: 327
Content-Type: text/plain; charset=utf-8
Date: Wed, 19 Dec 2018 10:52:05 GMT
Server: nginx/1.15.5

Hostname: a481c78f0bb7
IP: 127.0.0.1
IP: 172.23.0.3
GET / HTTP/1.1
Host: api
User-Agent: curl/7.54.0
Accept: */*
Accept-Encoding: gzip
Connection: close
X-Forwarded-For: 172.23.0.1
X-Forwarded-Host: api.localhost
X-Forwarded-Port: 80
X-Forwarded-Proto: http
X-Forwarded-Server: e244ed1d0ae0
X-Real-Ip: 172.23.0.1
```
