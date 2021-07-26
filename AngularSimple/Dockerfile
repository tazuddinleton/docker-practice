# Stage 1
FROM node:14-alpine as build-step
RUN mkdir -p /app
WORKDIR /app
COPY . .
RUN npm i && npm run build --prod

# Stage 2
FROM nginx:1.10-alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=build-step /app/dist/containerized .
ENTRYPOINT [ "nginx", "-g", "daemon off;" ]

