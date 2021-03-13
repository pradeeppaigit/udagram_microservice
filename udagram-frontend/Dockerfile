# From https://blog.knoldus.com/deployment-with-docker-in-ionic/
# Use NodeJS base image
FROM beevelop/ionic as ionic

# Create app directory
WORKDIR /usr/src/app

# Install app dependencies by copying
# package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy app source
COPY . .
RUN ionic build

# Get nginx image, delete default files, copy ionic to base nginx dir
FROM nginx:alpine
RUN rm -rf /usr/share/nginx/html/*
COPY --from=ionic /usr/src/app/www/ /usr/share/nginx/html/