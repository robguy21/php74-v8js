# All Credit to https://github.com/Cojecom/docker-php7.4-apache-v8js

This repository is simply a docker image that builds the above dockerfile so that you can use the following to integrate it into your project

### Your Dockerfile
Insert the below code into your dockerfile to have it working
```
FROM robguy21/php74-v8js:1.0.0 AS v8builder

COPY --from=v8builder /tmp/v8js.so /tmp/v8js.so
COPY --from=v8builder /opt/libv8/lib/ /opt/libv8/lib/
RUN mv /tmp/v8js.so "$(php -i | grep ^extension_dir | awk '{print $3}')"

RUN docker-php-ext-enable v8js
```
