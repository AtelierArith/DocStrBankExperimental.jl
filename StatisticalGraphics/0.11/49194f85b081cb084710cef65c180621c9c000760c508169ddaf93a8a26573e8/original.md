```
Violin(args...)
```

Represent a Violin Plot with given arguments.

# Keyword arguments

## Required

  * `x`: User should pass multiple columns for plotting the comparative violin plot, i.e. side by side violin plot for passed columns. User must pass either this or the `y` argument. default: `0`
  * `y`: User should pass multiple columns for plotting the comparative violin plot, i.e. side by side violin plot for passed columns. User must pass either this or the `x` argument. default: `0`

## Violin options

  * `bw`: The kernel bandwidth.
  * `categoryorder`: How the category should be ordered, i.e. `:ascending`, `:descending`, `:data`. default: `:ascending`
  * `interpolate`: The line interpolation algorithm for drawing the density line. default: `:linear`
  * `missingmode`: Indicate how to handle missing values in category or group.  `0` = nothing, `1` = no missing in category. default: `0`
  * `npoints`: The number of points for drawing the density line. default: `100`
  * `scale`: The scale to be used for density estimation, see `Density`. default: `StatisticalGraphics.violin_default_scale`
  * `weights`: The kernel weight function. default: `:gaussian`

## Grouping

  * `category`: A category column which indicates the violin plot must be drawn within each category.

## Violin appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function.
  * `filled`: Specifiy the plot should be filled with color. default: `true`
  * `fillopacity`: Specifiy The fill opacity of the plot. default: `0.5`
  * `groupspace`: The space between violins inside each category. It must be a number between 0 and 1. default: `0.05`
  * `opacity`: Specifiy The opacity of the density line. default: `1`
  * `side`: Specifiy which half of the violin plot should be plotted, i.e. `:right(:bottom)`, `:left(:top)`. default: `:both`
  * `space`: The space between violins. It must be a number between 0 and 1. default: `0.1`
  * `thickness`: Specifiy The thickness of the outline line. default: `1`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
