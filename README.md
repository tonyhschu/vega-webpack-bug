This repo isolates a bug when using webpack with vega and datalib.

To run, clone, then do the following.

```
$ npm install
$ webpack
```

What you should see is that acorn.js (parser used by webpack to parse stuff) chokes on
datalib's package.json ... which doesn't really make sense. `terminal-error.txt` contains the error output.

To temporarily fix it, I modified the `index.js` file in `node_modules/datalib/src/` and in `node_modules/vega/src` to remove the version line. Webpack stopped choking after that.

Not sure what a real fix should be, but apparently webpack and/or acorn doesn't like the `require('../package.json').version` notation.
