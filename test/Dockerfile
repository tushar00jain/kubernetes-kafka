FROM solsson/kafka:0.11.0.0@sha256:b27560de08d30ebf96d12e74f80afcaca503ad4ca3103e63b1fd43a2e4c976ce

RUN apt-get -y update && \
		apt-get -y upgrade

RUN apt-get -y install build-essential curl gzip libsasl2-dev python-dev python-setuptools vim

ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION v8.5.0

RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.4/install.sh | bash && \
		. $NVM_DIR/nvm.sh && \
		nvm install $NODE_VERSION && \
		nvm use $NODE_VERSION

ADD ./client /client

WORKDIR /client

ENV NODE_PATH $NVM_DIR/$NODE_VERSION/lib/node_modules
ENV PATH $NVM_DIR/versions/node/$NODE_VERSION/bin:$PATH
RUN npm install

ENTRYPOINT /bin/bash 