## docker-ssr-react

Originally cloned from https://github.com/thegreenhouseio/docker-ssr

This was a bit outdated to begin with, so I updated the dependencies and removed some code to make it work with the latest dependencies.

If you find a problem, please contact the original owner of this repo. Or open an issue, I will try my best to fix it.

The next section explains the workflow, which is retained from the original repository.



## Development
This repository provides a [**React**](https://reactjs.org/) project built with [**webpack**](https://webpack.js.org/) for development / testing purposes.  The intent is to act as a [fixture]() for what's defined in _Dockerfile_.

### Setup
1. [ ] Install [**Docker**](https://www.docker.com/products/docker-desktop)
1. [ ] Install [**NodeJS**](https://nodejs.org/en/) v8.x
1. [ ] Optionally, install [**Yarn**](https://yarnpkg.com/en/docs/install) 1.x

### Workflow
Development is mainly a two step process:

#### 1) UI Application
Develop with the React project and validate using available **npm** scripts (**Yarn** or **npm** supported):

- `yarn lint` - lint the project source code
- `yarn develop` - test changes with [**webpack-dev-server**](https://webpack.js.org/configuration/dev-server/)
- `yarn build` - build the client side assets for production
- `yarn serve` - build the client side assets and start the express server that has SSR enabled (without Docker)

#### 2) Docker
To validate the changes using the Docker container, first build the container
```shell
$ docker build -t ssr .
```

Then you can start it and view it at `http://localhost:3001`
```shell
$ docker run -p 3001:3001 -i -t ssr
```

You can also initiate a bash session to explore around after you've started it.  All files mounted are relative to `/`.
```shell
$ docker exec -it <ssr-app> bash
```

> See [this repo](https://github.com/thegreenhouseio/docker-nodejs-dev#development) for some additional Docker related workflows and commands.