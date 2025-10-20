ARG BUILD_FROM
FROM $BUILD_FROM

# Add env
ENV LANG C.UTF-8

# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN \
    apk add --no-cache \
        pulseaudio alsa-plugins-pulse bash \
    && rm -fr \
        /tmp/*

RUN apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/edge/community/ snapcast-server=0.34.0-r0

RUN apk add --no-cache --repository=http://dl-cdn.alpinelinux.org/alpine/edge/testing/ librespot=0.7.1-r0

RUN \
    wget https://github.com/badaix/snapweb/releases/download/v0.9.2/snapweb.zip && \
    unzip -o snapweb.zip -d /usr/share/snapserver/snapweb/ && \
    rm snapweb.zip

# Copy data for add-on
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]

