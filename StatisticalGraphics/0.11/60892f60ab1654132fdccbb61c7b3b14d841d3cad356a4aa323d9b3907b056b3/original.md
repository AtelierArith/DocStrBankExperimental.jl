```
Heatmap(args...)
```

Represent a Heatmap (2D Histogram) with given arguments.

# Keyword arguments

## Required

  * `x`: The column to be used as x coordinate. User must pass this and the `y` argument. default: `0`
  * `y`: The column to be used as y coordinate. User must pass this and the `x` argument. default: `0`

## Heatmap Options

  * `bincountmethod`: The number of points for the grid calculation in both direction. default: `StatisticalGraphics.default_bin_heatmap`
  * `tooltip`: A tooltip will be shown upon mouse hover. default: `false`
  * `xbincount`: The number of points for the grid calculation in x direction.
  * `ybincount`: The number of points for the grid calculation in y direction.

## Heatmap appearance

  * `colormodel`: Define the color model to be used for the heatmap plot. default: `:scheme => :viridis`
  * `opacity`: The opacity value for the outline. default: `1`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
