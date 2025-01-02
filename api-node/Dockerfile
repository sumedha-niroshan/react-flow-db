FROM node:19.6-bullseye-slim

ENV NODE_ENV production

WORKDIR /usr/src/app

COPY package*.json ./

# Install only production dependencies
RUN --mount=type=cache,target=/usr/src/app/.npm \
  npm set cache /usr/src/app/.npm && \
  npm ci --only=production

# Use non-root user
USER node

COPY --chown=node:node ./src/ .

EXPOSE 3000

CMD [ "node", "index.js" ]
