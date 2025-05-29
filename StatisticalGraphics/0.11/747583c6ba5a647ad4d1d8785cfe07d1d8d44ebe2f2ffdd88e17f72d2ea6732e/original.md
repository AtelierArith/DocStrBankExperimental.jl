```
Reg(args...)
```

Represent a Regression Line with given arguments.

# Keyword arguments

## Required

  * `x`: The column to be used as x, i.e. the independent variable. default: `0`
  * `y`: The column to be used as y, i.e. the response variable. default: `0`

## Reg Options

  * `degree`: The maximum polynomial degree for the fitted line. default: `1`
  * `intercept`: Whether the fitted line should have the intercept term. default: `true`
  * `interpolate`: The interplate function to use for drawing lines, e.g. `:linear`, `:basis`, `:natural`, `:step`, ... default: `:linear`
  * `npoints`: The number of points in grid for drawing the regression line. default: `100`

## Grouping

  * `group`: The name of column for grouping observation. Each group of observations will create seperate Regression Line.

## Reg appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `"#4682b4"`
  * `dash`: The Line dash style. default: `[0]`
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `thickness`: The Line thickness. default: `1`

## Confidence Interval

  * `alpha`: Control the confidence intervals level. default: `0.05`
  * `cli`: Draw the prediction confidence interval. default: `false`
  * `clicolor`: The filling color for the prediction confidence interval.
  * `cliopacity`: The opacity for the prediction confidence interval. default: `0.3`
  * `clm`: Draw the mean confidence interval. default: `false`
  * `clmcolor`: The filling color for the mean confidence interval.
  * `clmopacity`: The opacity for the mean confidence interval. default: `0.3`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
