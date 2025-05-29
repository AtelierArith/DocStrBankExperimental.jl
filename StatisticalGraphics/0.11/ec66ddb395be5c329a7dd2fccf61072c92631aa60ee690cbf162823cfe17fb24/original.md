```
Segment(args...)
```

Represent a Segment line with given arguments.

# Keyword arguments

## Required

  * `lower`: The lower values for segments. User can pass a column or a Float value. default: `0`
  * `upper`: The upper values for segments. User can pass a column or a Float value. default: `0`
  * `x`: The column to be used as x coordinate. User must pass either this or the `y` argument. default: `0`
  * `y`: The column to be used as y coordinate. User must pass either this or the `x` argument. default: `0`

## Grouping

  * `group`: The name of column for grouping observation. Each group of observations will create seperate segment lines.

## Segment appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `"#4682b4"`
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `thickness`: The thickness of the mark default: `1`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
