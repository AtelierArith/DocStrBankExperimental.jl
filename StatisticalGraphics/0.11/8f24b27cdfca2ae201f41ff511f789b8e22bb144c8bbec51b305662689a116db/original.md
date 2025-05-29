```
Density(args...)
```

Represent a Density plot with given arguments.

# Keyword arguments

## Required

  * `x`: The column to be used as x coordinate. User must pass either this or the `y` argument. default: `0`
  * `y`: The column to be used as y coordinate. User must pass either this or the `x` argument. default: `0`

## Density Options

  * `baseline`: The baseline for filling the curve. default: `0.0`
  * `bw`: Band width to be used in the kernel density estimation.
  * `interpolate`: The interplate function to use for drawing lines, e.g. `:linear`, `:basis`, `:natural`, `:step`, ... default: `:linear`
  * `npoints`: The number of points for the grid calculation. default: `100`
  * `scale`: user can pass any function to this option, the function must be in the form of `fun(density; midpoints, npoints, samplesize, binwidth)` , for `:pdf` the function is defined as `f(x; args...) = x`, for `:count` we compute the expected counts, `f(x; args...) = x .* binwidth .* npoints` , and for `:cdf` the function is `(x; binwidth, args...) -> cumsum(x .* binwidth)`. default: `:pdf`
  * `type`: Type of density fit, i.e. `:normal` or `:kernel`.  default: `:normal`
  * `weights`: The weighting function to be used when `:kernel` type is selected. default: `:gaussian`

## Grouping

  * `group`: The name of column for grouping observation. Each group of observations will create seperate density plot.

## Density appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function.
  * `fillcolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function.
  * `filled`: Indicate if the curve should be filled. default: `true`
  * `fillopacity`: The opacity value for the fill color. default: `0.5`
  * `opacity`: The opacity value for the outline. default: `1`
  * `thickness`: The mark outline thickness. default: `1`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
