##Stage 1 
FROM node:26-alpine as buildimage

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build


##Stage 2 build

FROM nginx:alpine

COPY --from=buildimage /app/dist /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

