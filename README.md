# komondor-plugin

[![NPM version][npm-image]][npm-url]
[![NPM downloads][downloads-image]][downloads-url]
[![Build status][travis-image]][travis-url]
[![Codecov][codecov-image]][codecov-url]
[![Coverage Status][coveralls-image]][coveralls-url]

[![Greenkeeper][greenkeeper-image]][greenkeeper-url]
[![Semantic Release][semantic-release-image]][semantic-release-url]

[![Visual Studio Code][vscode-image]][vscode-url]
[![Wallaby.js][wallaby-image]][wallaby-url]

Library to create plugin for [`komondor`](https://github.com/unional/komondor).

## Usage

To create plugin, you need to export a `activate()` function as follow:

```ts
import { Registrar } from 'komondor-plugin'

export function activate(registrar: Registrar) {
  registrar.register(...)
  // and/or
  registrar.registerForReturn(...)
}
```

The plugin should supply a `getSpy()` and `getStub()` function,
or `getReturnSpy()` and `getReturnStub()` function.

The `Spy` is used to record to actions performed,
while the `Stub` is used to replay the actions recorded.

The `ReturnSpy` and `ReturnStub` is used if the subject that cross the boundary is a return value of some other functions/methods.
For example `Promise` and `Stream`.

This library also provide some helper functions for creating plugins.

## createAction(type: string, payload, meta?): SpecAction

A simple helper to create action.

## createScopedCreateAction(actionType): (subType: string, payload, meta?) => SpecAction

Create a scoped `createAction()` for creating sub actions.
You will most likely to use this function to create a class of actions for a specific plugin.

## createExpectation(type: string, meta?): (payload) => SpecExpectation

`SpecExpectation` is a partial `SpecAction` to be used in a the `spec.satisfy()` call.

Use this function to create helper functions for the user to create their expectations easily.

## createScopedCreateExpectation(type: string): (subType: string, meta?) => (payload) => SpecExpectation

Create a scoped `createExpectation()`.

## Contribute

```sh
# right after fork
npm install

# begin making changes
git checkout -b <branch>
npm run watch

# edit `webpack.config.dev.js` to exclude dependencies for the global build.

# after making change(s)
git commit -m "<commit message>"
git push

# create PR
```

## Npm Commands

There are a few useful commands you can use during development.

```sh
# Run tests (and lint) automatically whenever you save a file.
npm run watch

# Run tests with coverage stats (but won't fail you if coverage does not meet criteria)
npm run test

# Manually verify the project.
# This will be ran during 'npm preversion' so you normally don't need to run this yourself.
npm run verify

# Build the project.
# You normally don't need to do this.
npm run build

# Run tslint
# You normally don't need to do this as `npm run watch` and `npm version` will automatically run lint for you.
npm run lint
```

Generated by `generator-unional@0.0.1`

## TODO

- [ ] work on browser

[npm-image]: https://img.shields.io/npm/v/komondor-plugin.svg?style=flat
[npm-url]: https://npmjs.org/package/komondor-plugin
[downloads-image]: https://img.shields.io/npm/dm/komondor-plugin.svg?style=flat
[downloads-url]: https://npmjs.org/package/komondor-plugin
[travis-image]: https://img.shields.io/travis/unional/komondor-plugin/master.svg?style=flat
[travis-url]: https://travis-ci.org/unional/komondor-plugin?branch=master
[codecov-image]: https://codecov.io/gh/unional/komondor-plugin/branch/master/graph/badge.svg
[codecov-url]: https://codecov.io/gh/unional/komondor-plugin
[coveralls-image]: https://coveralls.io/repos/github/unional/komondor-plugin/badge.svg
[coveralls-url]: https://coveralls.io/github/unional/komondor-plugin
[green-keeper-image]:
https://badges.greenkeeper.io/unional/komondor-plugin.svg
[green-keeper-url]:https://greenkeeper.io/
[semantic-release-image]:https://img.shields.io/badge/%20%20%F0%9F%93%A6%F0%9F%9A%80-semantic--release-e10079.svg
[semantic-release-url]:https://github.com/semantic-release/semantic-release
