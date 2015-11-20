# PostCSS Bidirection [![Build Status][ci-img]][ci]

[PostCSS] plugin that polyfill Bi-directional CSS proposal to suppot direction-sensitive rules, a.k.a Left-To-Right (LTR) and Right-To-Left (RTL), in single syntax.

This CSS syntax is [already in production](https://github.com/mozilla-b2g/gaia/blob/master/apps/settings/style/settings.css) in Mozilla's [Firefox OS](https://www.mozilla.org/en-US/firefox/os/), which could be installed as an Android launcher. Once its started, open Settings > Language and choose an sample RTL Language to check the result.

[PostCSS]: https://github.com/postcss/postcss
[ci-img]:  https://travis-ci.org/gasolin/postcss-bidirection.svg
[ci]:      https://travis-ci.org/gasolin/postcss-bidirection

## Install

```
npm install --save-dev postcss-bidirection
```

## Usage

Install postcss-bidirection via npm:

```js
postcss([ require('postcss-bidirection') ])
```

See [PostCSS] docs for examples for your environment.

To check the layout change, in your HTML file, add attribute in your html tags

```
<html dir="rtl">

```

Or, in your js file, set `document.dir = 'rtl'` or `document.dir = 'ltr'`.


## Examples

PostCSS Bidirection support syntax based on https://wiki.mozilla.org/Gaia/CSS_Guidelines

### Text alignment example

Input

```css
.foo {
  text-align: start;
}
```

Output

```css
.foo {
  text-align: left;
}

html[dir="rtl"] .foo {
  text-align: right;
}
```

### Padding Example

Input

```css
.foo {
  padding-inline-start: 1px;
}
```

Output

```css
.foo {
  padding-left: 1px;
}

html[dir="rtl"] .foo {
  padding-right: 1px;
}
```

## Absolute Positioning Example

Input

```css
.foo {
  offset-inline-start: 1px;
}
```

Output

```css
.foo {
  left: 1px;
}

html[dir="rtl"] .foo {
  right: 1px;
}
```


All supported syntax are listed below

|     left/right     |     begin/end        |
|--------------------|----------------------|
|             **text alignment**            |
| text-align: left   | text-align: start    |
| text-align: right  | text-align: end      |
|       **padding, margin, border**         |
| padding-left       | padding-inli ne-start |
| padding-right      | padding-inline-end   |
| border-left        | border-inline-start  |
| border-right       | border-inline-end    |
| margin-left        | margin-inline-start  |
| margin-right       | margin-inline-end    |
|         **absolute positioning**          |
| left               | offset-inline-start  |
| right              | offset-inline-end    |
