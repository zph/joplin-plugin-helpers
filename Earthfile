FROM node:lts-bullseye
WORKDIR /srv

deps:
  COPY ./ .
  RUN npm install
  RUN apt-get update
  RUN apt-get install pre-commit

test:
  FROM +deps
  RUN pre-commit run --all-files

build:
  FROM +deps
  RUN npm run dist
  RUN sha256sum publish/* > publish/sha256sum.txt
  SAVE ARTIFACT publish AS LOCAL publish
