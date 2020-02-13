FROM python:3.7-slim

LABEL Description='Defcon Workshop image'
LABEL maintainer='aryabchi <cyberxx@yandex.ru>'

ENV PYTHONBUFERED=true
ENV PYTHONDONOTWRITEBYTECODE=true

WORKDIR /home/docker/code/app

RUN apt-get update && apt-get install -y libpq-dev gcc make

RUN pip install -U poetry==0.12.10 --no-cache-dir && \
 poetry config settings.virtualenvs.create false

COPY ./pyproject.toml /home/docker/code/app/
RUN poetry install

COPY . /home/docker/code/app
COPY ./docker/app/gunicorn.py /

EXPOSE 80
