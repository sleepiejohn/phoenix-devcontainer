FROM hexpm/elixir:1.11.2-erlang-23.1-ubuntu-groovy-20201022.1

ARG PHOENIX_VERSION=1.5.7
ARG USER_UID=1000
ARG USER_GID=$USER_UID


# NodeJS

RUN apt-get install -y g++ make gcc inotify-tools git curl
RUN curl -sL https://deb.nodesource.com/setup_lts.x | bash - \
    && DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs \
    && rm -rf /var/cache/apt \
    && npm install -g yarn


# Finish up Elixir and Phoenix
RUN mix local.hex --force && mix local.rebar --force
RUN mix archive.install hex phx_new $PHOENIX_VERSION --force

