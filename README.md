[![Build Status](https://travis-ci.org/saranonearth/demo.svg?branch=master)](https://travis-ci.org/saranonearth/demo)
## cicd-travis-aws-docker



travis.yaml
```
language: node_js

node_js:
  - "8"

sudo: required
services:
  - docker

before_install:
  - docker build -t saranonearth/demo -f Dockerfile.dev .

script:
  - docker run -e CI=true saranonearth/demo npm run test

deploy:
  provider: elasticbeanstalk
  access_key_id: $ACCESSKEYID
  secret_access_key: $SECRETACCESSKEY
  region: "ap-south-1"
  app: ""
  env: ""
  bucket_name: ""
  bucket_path: ""
  on:
    branch: master
```
