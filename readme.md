# create-inferno-library

> CLI for creating reusable, modern Inferno libraries using Rollup and create-inferno-app.

[![NPM](https://img.shields.io/npm/v/create-inferno-library.svg)](https://www.npmjs.com/package/create-inferno-library) [![Build Status](https://travis-ci.com/tbjgolden/create-inferno-library.svg?branch=master)](https://travis-ci.com/tbjgolden/create-inferno-library) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

This is a fork of [`create-react-library`](https://github.com/transitive-bullshit/create-react-library).
At the moment, it doesn't offer a Typescript option like `create-react-library`, but if you'd like to have it,
let me know, or send up a pull request :)

## Intro

<p align="center">
  <img width="600" src="https://cdn.rawgit.com/tbjgolden/create-inferno-library/master/media/demo.svg">
</p>

## Features

- Easy-to-use CLI
- Handles all modern JS features
- Bundles `cjs` and `es` module formats
- [create-inferno-app](https://github.com/infernojs/create-inferno-app) for example usage and local dev
- [Rollup](https://rollupjs.org/) for bundling
- [Babel](https://babeljs.io/) for transpiling
- [Jest](https://infernojs.github.io/jest/) for testing
- Supports complicated peer-dependencies
- Supports CSS modules
- Optional support for TypeScript
- Sourcemap creation
- Hundreds of public modules created
- Thorough documentation :heart_eyes:

## Install globally

This package requires `node >= 4`, but we recommend `node >= 8`.

```bash
yarn global add create-inferno-library
# OR npm install -g create-inferno-library
```

## Usage with npx

```bash
npx create-inferno-library
```

_([npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) comes with npm 5.2+ and higher, see [instructions for older npm versions](https://gist.github.com/gaearon/4064d3c23a77c74a3614c498a8bb1c5f))_

## Creating a New Module

```bash
create-inferno-library
```

Answer some basic prompts about your module, and then the CLI will perform the following steps:
- copy over the template
- install dependencies via yarn or npm
- link packages together for local development
- initialize local git repo

At this point, your new module should resemble this screenshot and is all setup for local development.

<p align="center">
  <img width="600" src="https://cdn.rawgit.com/tbjgolden/create-inferno-library/master/media/tree.svg">
</p>


## Development

Local development is broken into two parts (ideally using two tabs).

First, run rollup to watch your `src/` module and automatically recompile it into `dist/` whenever you make changes.

```bash
yarn start
# OR npm start
# runs rollup with watch flag
```

The second part will be running the `example/` create-inferno-app that's linked to the local version of your module.

```bash
# (in another shell)
cd example
yarn start
# OR npm start
# runs create-inferno-app dev server
```

Now, anytime you make a change to your library in `src/` or to the example app's `example/src`, `create-inferno-app` will live-reload your local dev server so you can iterate on your component in real-time.

![](https://media.giphy.com/media/12NUbkX6p4xOO4/giphy.gif)


#### Publishing to npm

```bash
npm publish
```

This builds `cjs` and `es` versions of your module to `dist/` and then publishes your module to `npm`.

Make sure that any npm modules you want as peer dependencies are properly marked as `peerDependencies` in `package.json`. The rollup config will automatically recognize them as peers and not try to bundle them in your module.


#### Deploying to Github Pages

```bash
yarn deploy
# OR npm run deploy
```

This creates a production build of the example `create-inferno-app` that showcases your library and then runs `gh-pages` to deploy the resulting bundle.

## Examples

### Multiple Named Exports

Here is a [branch](https://github.com/tbjgolden/inferno-modern-library-boilerplate/tree/feature/multiple-exports) which demonstrates how to use multiple named exports. The module in this branch exports two components, `Foo` and `Bar`, and shows how to use them from the example app.

### Material-UI

Here is a [branch](https://github.com/tbjgolden/inferno-modern-library-boilerplate/tree/feature/material-ui) which demonstrates how to make use of a relatively complicated peer dependency, [material-ui](https://github.com/mui-org/material-ui). It shows the power of [rollup-plugin-peer-deps-external](https://www.npmjs.com/package/rollup-plugin-peer-deps-external) which makes it a breeze to create reusable modules that include complicated material-ui subcomponents without having them bundled as a part of your module.

### Boilerplate

The CLI is based on this [boilerplate](https://github.com/tbjgolden/inferno-modern-library-boilerplate), which you can optionally read about [here](https://hackernoon.com/publishing-baller-inferno-modules-2b039d84bce7).

### Libraries

Here are some example libraries that have been bootstrapped with `create-inferno-library`.

- [`inferno-google-recaptcha-v3`](https://github.com/tbjgolden/inferno-google-recaptcha-v3)

Want to add yours to the list? Submit an [issue](https://github.com/tbjgolden/create-inferno-library/issues/new).

## License

MIT © [Tom Golden](https://github.com/tbjgolden)

Thanks to [Travis Fischer](https://github.com/transitive-bullshit) for making create-react-library.
