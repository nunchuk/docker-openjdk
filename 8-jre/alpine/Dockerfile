############################################################ 
# Dockerfile to build image OpenJDK
# Based on alpine:3.5
############################################################

FROM library/openjdk:8-jre-alpine
MAINTAINER XinYe <nunchuk@live.com>

# add AliCloud repository
# > If you are using Aliyun ECS, the package mirror server can be replaced by 
# > 'mirrors.cloud.aliyuncs.com', via Aliyun private network.
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories

ENV TIMEZONE=Asia/Shanghai \
	TIMEZONE_DEPS=tzdata

# set timezone
RUN set -xe; \
	apk --update add --no-cache --virtual .build-deps \
                      $TIMEZONE_DEPS ; \
	cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime ; \
	echo ${TIMEZONE} > /etc/timezone

# clean up
RUN apk del .build-deps && \
	rm -rf /var/cache/apk/*