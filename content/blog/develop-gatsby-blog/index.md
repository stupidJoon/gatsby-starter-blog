---
title: Gatsby로 블로그 만들기
date: "2022-12-25 22:55:00"
---

Gatsby에서 제공하는 gatsby-starter-blog를 가져와서 구현해 보겠다.

## 0. 기본 패키지 설치하기
```bash
npm i -g gatsby-cli
```

## 1. gatsby-starter-blog 가져오기
```bash
gatsby new gatsby-starter-blog https://github.com/gatsbyjs/gatsby-starter-blog
```

## 2. github pages에 배포하기

### 2-1. username.github.io repo 만들기
`username`.github.io 제목으로 github repo를 만든다

### 2-2. Github Actions으로 배포 자동화하기


```yaml
name: Deploy Gatsby To Github Pages

on:
  push:
    branches: ["master"]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: actions/setup-node@v3
        with:
          node-version: '18'
      - uses: enriikke/gatsby-gh-pages-action@v2
        with:
          access-token: ${{ secrets.ACCESS_TOKEN }}
          deploy-repo: "username.github.io"

```
