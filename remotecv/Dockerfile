ARG THUMBOR_TAG=latest
FROM minimalcompact/thumbor:$THUMBOR_TAG

LABEL maintainer="MinimalCompact"

VOLUME /data

ENV HOME /app
ENV SHELL bash
ENV WORKON_HOME /app
WORKDIR /app

COPY requirements.txt /app/requirements.txt
#https://github.com/Kozea/CairoSVG/issues/232 解决CairoSVG 1.0.22 install broken with pip on Python 2.7
RUN pip install -U pip -i https://pypi.tuna.tsinghua.edu.cn/simple

RUN pip install -i https://pypi.tuna.tsinghua.edu.cn/simple --trusted-host None --no-cache-dir \
   -r /app/requirements.txt

COPY docker-entrypoint.sh /
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["remotecv"]
