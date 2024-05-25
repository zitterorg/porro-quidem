# @zitterorg/porro-quidem <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2017 spec-compliant `Object.values` shim. Invoke its "shim" method to shim `Object.values` if it is unavailable or noncompliant.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.github.io/ecma262/#sec-@zitterorg/porro-quidem).

Most common usage:
```js
var assert = require('assert');
var values = require('@zitterorg/porro-quidem');

var obj = { a: 1, b: 2, c: 3 };
var expected = [1, 2, 3];

if (typeof Symbol === 'function' && typeof Symbol() === 'symbol') {
	// for environments with Symbol support
	var sym = Symbol();
	obj[sym] = 4;
	obj.d = sym;
	expected.push(sym);
}

assert.deepEqual(values(obj), expected);

if (!Object.values) {
	values.shim();
}

assert.deepEqual(Object.values(obj), expected);
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.com/package/@zitterorg/porro-quidem
[npm-version-svg]: https://versionbadg.es/zitterorg/porro-quidem.svg
[deps-svg]: https://david-dm.org/zitterorg/porro-quidem.svg
[deps-url]: https://david-dm.org/zitterorg/porro-quidem
[dev-deps-svg]: https://david-dm.org/zitterorg/porro-quidem/dev-status.svg
[dev-deps-url]: https://david-dm.org/zitterorg/porro-quidem#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/@zitterorg/porro-quidem.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/@zitterorg/porro-quidem.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/@zitterorg/porro-quidem.svg
[downloads-url]: https://npm-stat.com/charts.html?package=@zitterorg/porro-quidem
[codecov-image]: https://codecov.io/gh/zitterorg/porro-quidem/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/zitterorg/porro-quidem/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/zitterorg/porro-quidem
[actions-url]: https://github.com/zitterorg/porro-quidem/actions
