FROM node:alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN npm install
COPY ./ ./
RUN npm run build

FROM nginx
# 컨테이너가 3000번 포트 listen 중
EXPOSE 3000
# 컨테이너 안에 있는 nginx 설정 파일을 덮어 쓴다
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# /usr/share/nginx/html: default.conf의 root 경로와 동일
COPY --frin=builder /app/build /usr/share/nginx/html