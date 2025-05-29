```
RefLine(args...)
```

Represent a Refline with given arguments.

# Keyword arguments

## Required

  * `axis`: WHich axis should be used to draw the reflines, i.e. `:xaxis`, `:x2axis`, `:yaxis`, `:y2axis`.
  * `values`: The position of reflines, it can be a vector of values. default: `0`

## Refline appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `:grey`
  * `dash`: The line dash style. default: `[0]`
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `thickness`: The line thickness. default: `1`

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
