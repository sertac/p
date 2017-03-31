FROM python:3.5
WORKDIR /opt/p
COPY requirements.txt requirements.txt
RUN pip install uwsgi -r requirements.txt
COPY . .
RUN groupadd -r -g 999 application && \
    useradd -r -g application application && \
    chown -R application:application .
RUN mkdir /run/p && \
    chown application:application /run/p
VOLUME /opt/p \
       /run/p
CMD uwsgi config/application/uwsgi.ini
