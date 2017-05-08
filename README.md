# postcss-plugin-bem-escape-block-name-less-modifier [![Build Status][travis-image]][travis-url] [![Coverage percentage][coveralls-image]][coveralls-url]

this [PostCSS] plugin fixes minor problems in modifier class without block name in BEM(exactly MindBEMding).

> this plugin was created to solve the problem of a specific context (block-name-less modifier), it is not designed to escape the css selector generically.

this [PostCSS] plugin will transform this:

```css
.blcok.--modifier-a.--modifier-b {
    ...
}
```

To this:

```css
.blcok.\--modifier-a.\--modifier-b {
    ...
}
```

## installation

```bash
npm i -D postcss-plugin-bem-escape-block-name-less-modifier
```

## usage

```js
postcss([ require('postcss-plugin-bem-escape-block-name-less-modifier') ])
```

## problem and solution

in the specification of selector name of css, if there is a hyphen (-) first, it is supposed not to specify a hyphen successively.

a strict web browser about this specification will not recognize such a class name. (ie, old android browser, etc)

so this plugin solves this problem by escaping the first letter of the class name in this pattern.

## why use a modifier without a block name ?

when css is written in MindBEMding, if the modifier gets complicated, your html will be very ugly.

(the css file can be solved with a preprocessor like sass!)

```html
<div class="my-important-class  my-important-class--active  my-important-class--danger  my-important-class--strong">
```

so i omit the modifier block name.

when writing like this with sass...

```scss
.my-important-class {
   &.--active {...}
   &.--danger {...}
   &.--strong {...}
}
/**
output:
.my-important-class.--active { ... }
.my-important-class.--danger { ... }
.my-important-class.--strong { ... }
**/
```

html will be so cute! It is!

```html
<div class = "my-important-class  --active  --danger  --strong">
```


[![NPM](https://nodei.co/npm/postcss-plugin-bem-escape-block-name-less-modifier.png?downloads=true&downloadRank=true&stars=true)](https://nodei.co/npm/gitbook-plugin-search-languages/)

[coveralls-image]: https://coveralls.io/repos/yoshidax/postcss-plugin-bem-escape-block-name-less-modifier/badge.svg
[coveralls-url]: https://coveralls.io/r/yoshidax/postcss-plugin-bem-escape-block-name-less-modifier
[travis-image]: https://travis-ci.org/yoshidax/postcss-plugin-bem-escape-block-name-less-modifier.svg?branch=master
[travis-url]: https://travis-ci.org/yoshidax/postcss-plugin-bem-escape-block-name-less-modifier
[PostCSS]: https://github.com/postcss/postcss
