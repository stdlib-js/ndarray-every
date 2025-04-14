<!--

@license Apache-2.0

Copyright (c) 2025 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->


<details>
  <summary>
    About stdlib...
  </summary>
  <p>We believe in a future in which the web is a preferred environment for numerical computation. To help realize this future, we've built stdlib. stdlib is a standard library, with an emphasis on numerical and scientific computation, written in JavaScript (and C) for execution in browsers and in Node.js.</p>
  <p>The library is fully decomposable, being architected in such a way that you can swap out and mix and match APIs and functionality to cater to your exact preferences and use cases.</p>
  <p>When you use stdlib, you can be absolutely certain that you are using the most thorough, rigorous, well-written, studied, documented, tested, measured, and high-quality code out there.</p>
  <p>To join us in bringing numerical computing to the web, get started by checking us out on <a href="https://github.com/stdlib-js/stdlib">GitHub</a>, and please consider <a href="https://opencollective.com/stdlib">financially supporting stdlib</a>. We greatly appreciate your continued support!</p>
</details>

# every

[![NPM version][npm-image]][npm-url] [![Build Status][test-image]][test-url] [![Coverage Status][coverage-image]][coverage-url] <!-- [![dependencies][dependencies-image]][dependencies-url] -->

> Test whether every element along one or more [`ndarray`][@stdlib/ndarray/ctor] dimensions is truthy.

<section class="intro">

</section>

<!-- /.intro -->



<section class="usage">

## Usage

To use in Observable,

```javascript
every = require( 'https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-every@umd/browser.js' )
```

To vendor stdlib functionality and avoid installing dependency trees for Node.js, you can use the UMD server build:

```javascript
var every = require( 'path/to/vendor/umd/ndarray-every/index.js' )
```

To include the bundle in a webpage,

```html
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/ndarray-every@umd/browser.js"></script>
```

If no recognized module system is present, access bundle contents via the global scope:

```html
<script type="text/javascript">
(function () {
    window.every;
})();
</script>
```

#### every( x\[, options] )

Tests whether every element along one or more [`ndarray`][@stdlib/ndarray/ctor] dimensions is truthy.

<!-- eslint-disable max-len -->

```javascript
var Float64Array = require( '@stdlib/array-float64' );
var ndarray = require( '@stdlib/ndarray-ctor' );

// Create a data buffer:
var xbuf = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

// Define the shape of the input array:
var sh = [ 3, 1, 2 ];

// Define the array strides:
var sx = [ 4, 4, 1 ];

// Define the index offset:
var ox = 1;

// Create an input ndarray:
var x = new ndarray( 'float64', xbuf, sh, sx, ox, 'row-major' );

// Test elements:
var out = every( x );
// returns <ndarray>

var v = out.get();
// returns true
```

The function accepts the following arguments:

-   **x**: input [`ndarray`][@stdlib/ndarray/ctor].
-   **options**: function options (_optional_).

The function accepts the following `options`:

-   **dims**: list of dimensions over which to perform a reduction.
-   **keepdims**: boolean indicating whether the reduced dimensions should be included in the returned [`ndarray`][@stdlib/ndarray/ctor] as singleton dimensions. Default: `false`.

By default, the function performs a reduction over all elements in a provided [`ndarray`][@stdlib/ndarray/ctor]. To reduce specific dimensions, set the `dims` option.

<!-- eslint-disable max-len -->

```javascript
var Float64Array = require( '@stdlib/array-float64' );
var ndarray = require( '@stdlib/ndarray-ctor' );
var ndarray2array = require( '@stdlib/ndarray-to-array' );

// Create a data buffer:
var xbuf = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

// Define the shape of the input array:
var sh = [ 3, 1, 2 ];

// Define the array strides:
var sx = [ 4, 4, 1 ];

// Define the index offset:
var ox = 1;

// Create an input ndarray:
var x = new ndarray( 'float64', xbuf, sh, sx, ox, 'row-major' );

// Test elements:
var out = every( x, {
    'dims': [ 1, 2 ]
});
// returns <ndarray>

var v = ndarray2array( out );
// returns [ true, true, true ]
```

By default, the function returns an [`ndarray`][@stdlib/ndarray/ctor] having a shape matching only the non-reduced dimensions of the input [`ndarray`][@stdlib/ndarray/ctor] (i.e., the reduced dimensions are dropped). To include the reduced dimensions as singleton dimensions in the output [`ndarray`][@stdlib/ndarray/ctor], set the `keepdims` option to `true`.

<!-- eslint-disable max-len -->

```javascript
var Float64Array = require( '@stdlib/array-float64' );
var ndarray = require( '@stdlib/ndarray-ctor' );
var ndarray2array = require( '@stdlib/ndarray-to-array' );

// Create a data buffer:
var xbuf = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

// Define the shape of the input array:
var sh = [ 3, 1, 2 ];

// Define the array strides:
var sx = [ 4, 4, 1 ];

// Define the index offset:
var ox = 1;

// Create an input ndarray:
var x = new ndarray( 'float64', xbuf, sh, sx, ox, 'row-major' );

// Test elements:
var out = every( x, {
    'dims': [ 1, 2 ],
    'keepdims': true
});
// returns <ndarray>

var v = ndarray2array( out );
// returns [ [ [ true ] ], [ [ true ] ], [ [ true ] ] ]
```

#### every.assign( x, out\[, options] )

Tests whether every element along one or more [`ndarray`][@stdlib/ndarray/ctor] dimensions is truthy and assigns results to a provided output [`ndarray`][@stdlib/ndarray/ctor].

<!-- eslint-disable max-len -->

```javascript
var Float64Array = require( '@stdlib/array-float64' );
var ndarray = require( '@stdlib/ndarray-ctor' );
var empty = require( '@stdlib/ndarray-empty' );

// Create a data buffer:
var xbuf = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

// Define the shape of the input array:
var sh = [ 3, 1, 2 ];

// Define the array strides:
var sx = [ 4, 4, 1 ];

// Define the index offset:
var ox = 1;

// Create an input ndarray:
var x = new ndarray( 'float64', xbuf, sh, sx, ox, 'row-major' );

// Create an output ndarray:
var y = empty( [], {
    'dtype': 'bool'
});

// Test elements:
var out = every.assign( x, y );
// returns <ndarray>

var bool = ( out === y );
// returns true

var v = y.get();
// returns true
```

The function accepts the following arguments:

-   **x**: input [`ndarray`][@stdlib/ndarray/ctor].
-   **out**: output [`ndarray`][@stdlib/ndarray/ctor]. The output [`ndarray`][@stdlib/ndarray/ctor] must have a shape matching the non-reduced dimensions of the input [`ndarray`][@stdlib/ndarray/ctor].
-   **options**: function options (_optional_).

The function accepts the following `options`:

-   **dims**: list of dimensions over which to perform a reduction.

By default, the function performs a reduction over all elements in a provided [`ndarray`][@stdlib/ndarray/ctor]. To reduce specific dimensions, set the `dims` option.

<!-- eslint-disable max-len -->

```javascript
var Float64Array = require( '@stdlib/array-float64' );
var ndarray = require( '@stdlib/ndarray-ctor' );
var empty = require( '@stdlib/ndarray-empty' );
var ndarray2array = require( '@stdlib/ndarray-to-array' );

// Create a data buffer:
var xbuf = new Float64Array( [ 1.0, 2.0, 3.0, 4.0, 5.0, 6.0, 7.0, 8.0, 9.0, 10.0, 11.0, 12.0 ] );

// Define the shape of the input array:
var sh = [ 3, 1, 2 ];

// Define the array strides:
var sx = [ 4, 4, 1 ];

// Define the index offset:
var ox = 1;

// Create an input ndarray:
var x = new ndarray( 'float64', xbuf, sh, sx, ox, 'row-major' );

// Create an output ndarray:
var y = empty( [ 3 ], {
    'dtype': 'bool'
});

// Test elements:
var out = every.assign( x, y, {
    'dims': [ 1, 2 ]
});

var bool = ( out === y );
// returns true

var v = ndarray2array( y );
// returns [ true, true, true ]
```

</section>

<!-- /.usage -->

<section class="notes">

</section>

<!-- /.notes -->

<section class="examples">

## Examples

<!-- eslint no-undef: "error" -->

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script type="text/javascript" src="https://cdn.jsdelivr.net/gh/stdlib-js/random-base-bernoulli@umd/browser.js"></script>
<script type="text/javascript">
(function () {.factory;
var ndarray2array = require( '@stdlib/ndarray-to-array' );
var fillBy = require( '@stdlib/ndarray-fill-by' );
var zeros = require( '@stdlib/ndarray-zeros' );
var every = require( '@stdlib/ndarray-every' );

var x = zeros( [ 2, 4, 5 ], {
    'dtype': 'float64'
});
x = fillBy( x, bernoulli( 0.90 ) );
console.log( ndarray2array( x ) );

var y = every( x );
console.log( 'every(x[:,:,:]) =' );
console.log( y.get() );

y = every( x, {
    'dims': [ 0 ],
    'keepdims': true
});
console.log( 'every(x[:,j,k]) =' );
console.log( ndarray2array( y ) );

y = every( x, {
    'dims': [ 1 ],
    'keepdims': true
});
console.log( 'every(x[i,:,k]) =' );
console.log( ndarray2array( y ) );

y = every( x, {
    'dims': [ 2 ],
    'keepdims': true
});
console.log( 'every(x[i,j,:]) =' );
console.log( ndarray2array( y ) );

y = every( x, {
    'dims': [ 0, 1 ],
    'keepdims': true
});
console.log( 'every(x[:,:,k]) =' );
console.log( ndarray2array( y ) );

y = every( x, {
    'dims': [ 0, 2 ],
    'keepdims': true
});
console.log( 'every(x[:,j,:]) =' );
console.log( ndarray2array( y ) );

y = every( x, {
    'dims': [ 1, 2 ],
    'keepdims': true
});
console.log( 'every(x[i,:,:]) =' );
console.log( ndarray2array( y ) );

y = every( x, {
    'dims': [ 0, 1, 2 ],
    'keepdims': true
});
console.log( 'every(x[:,:,:]) =' );
console.log( ndarray2array( y ) );

})();
</script>
</body>
</html>
```

</section>

<!-- /.examples -->

<!-- Section for related `stdlib` packages. Do not manually edit this section, as it is automatically populated. -->

<section class="related">

</section>

<!-- /.related -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

#### Community

[![Chat][chat-image]][chat-url]

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2025. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[npm-image]: http://img.shields.io/npm/v/@stdlib/ndarray-every.svg
[npm-url]: https://npmjs.org/package/@stdlib/ndarray-every

[test-image]: https://github.com/stdlib-js/ndarray-every/actions/workflows/test.yml/badge.svg?branch=main
[test-url]: https://github.com/stdlib-js/ndarray-every/actions/workflows/test.yml?query=branch:main

[coverage-image]: https://img.shields.io/codecov/c/github/stdlib-js/ndarray-every/main.svg
[coverage-url]: https://codecov.io/github/stdlib-js/ndarray-every?branch=main

<!--

[dependencies-image]: https://img.shields.io/david/stdlib-js/ndarray-every.svg
[dependencies-url]: https://david-dm.org/stdlib-js/ndarray-every/main

-->

[chat-image]: https://img.shields.io/gitter/room/stdlib-js/stdlib.svg
[chat-url]: https://app.gitter.im/#/room/#stdlib-js_stdlib:gitter.im

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[umd]: https://github.com/umdjs/umd
[es-module]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules

[deno-url]: https://github.com/stdlib-js/ndarray-every/tree/deno
[deno-readme]: https://github.com/stdlib-js/ndarray-every/blob/deno/README.md
[umd-url]: https://github.com/stdlib-js/ndarray-every/tree/umd
[umd-readme]: https://github.com/stdlib-js/ndarray-every/blob/umd/README.md
[esm-url]: https://github.com/stdlib-js/ndarray-every/tree/esm
[esm-readme]: https://github.com/stdlib-js/ndarray-every/blob/esm/README.md
[branches-url]: https://github.com/stdlib-js/ndarray-every/blob/main/branches.md

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/ndarray-every/main/LICENSE

[@stdlib/ndarray/ctor]: https://github.com/stdlib-js/ndarray-ctor/tree/umd

<!-- <related-links> -->

<!-- </related-links> -->

</section>

<!-- /.links -->
