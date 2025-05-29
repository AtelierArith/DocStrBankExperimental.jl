```
tidysvg(fname)
```

Read the SVG image in `fname` and write it to a file `fname-tidy.svg` with modified glyph names.

Return the name of the modified file.

SVG images use 'named defs' for text, which cause errors problem when used in browsers and notebooks. See [this github issue](https://github.com/jupyter/notebook/issues/333) for details.

A kludgy workround is to rename the elements.
