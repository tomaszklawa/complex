
FROM node:16-alpine 

WORKDIR '/app'

COPY ./package.json /app/package.json

RUN npm config set unsafe-perm true
RUN npm install
RUN mkdir -p node_modules/.cache && chmod -R 777 node_modules/.cache

COPY . .

RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html

#CMD ["npm","run","start"]



