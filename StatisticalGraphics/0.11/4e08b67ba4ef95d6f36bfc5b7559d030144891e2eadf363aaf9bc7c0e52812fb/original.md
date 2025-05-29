```
Histogram(args...)
```

Represent a Histogram with given arguments.

# Keyword arguments

## Required

  * `x`: The column to be used as x coordinate. User must pass either this or the `y` argument. default: `0`
  * `y`: The column to be used as y coordinate. User must pass either this or the `x` argument. default: `0`

## Histogram Options

  * `midpoints`: The location of midpoints. It can be a number to indicate the number of midpoints or a vector of midpoints. default: `:Sturges`
  * `scale`: The scale to use for the bar heights, e.g. `:pdf`, `:cdf`, `:count`. default: `:pdf`

## Grouping

  * `group`: The name of column for grouping observation. Each group of observations will create seperate histogram plot.

## Histogram appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `"#4682b4"`
  * `opacity`: The opacity value for the outline. default: `1`
  * `outlinecolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `:white`
  * `outlinethickness`: The outline thickness. default: `1`
  * `space`: Space between bars in pixel. default: `1`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
