```
BoxPlot(args...)
```

Represent a Box Plot with given arguments.

# Keyword arguments

## Required

  * `x`: User should pass multiple columns for plotting the comparative box plot, i.e. side by side box plot for passed columns. User must pass either this or the `y` argument. default: `0`
  * `y`: User should pass multiple columns for plotting the comparative box plot, i.e. side by side box plot for passed columns. User must pass either this or the `x` argument. default: `0`

## BoxPlot options

  * `categoryorder`: How the category should be ordered, i.e. `:ascending`, `:descending`, `:data`. default: `:ascending`
  * `missingmode`: Indicate how to handle missing values in category or group.  `0` = nothing, `1` = no missing in category. default: `0`
  * `outliers`: If `true` the oultliers will be shown. The outliers are computed based on how many `outliersfactor` they are far from quartiles. default: `false`
  * `outliersfactor`: The factor to be used for computing outliers. default: `1.5`

## Grouping

  * `category`: A category column which indicates the box plot must be drawn within each category.

## BoxPlot appearance

  * `boxcorner`: Corner radius for boxes. (`cornerRadiusTopLeft`, `cornerRadiusTopRight`, `cornerRadiusBottomLeft`, `cornerRadiusBottomRight`). default: `0`
  * `boxwidth`: The box width, it must be a number between 0 and 1. default: `1`
  * `fencecolor`: Specifiy the color for the fence lines. default: `:black`
  * `fencewidth`: Specifiy the total width for the fence lines. It must be a number between 0 and 1. default: `0.5`
  * `groupspace`: The space between boxes inside each category. It must be a number between 0 and 1. default: `0.05`
  * `meansymbol`: Specifiy the symbol to be used for the mean indicator. default: `:diamond`
  * `meansymbolsize`: Specifiy the symbol size to be used for the mean indicator. default: `40`
  * `mediancolor`: Specifiy the color for the median indicator. default: `:white`
  * `medianthickness`: Specifiy the thickness for the median indicator. default: `1`
  * `medianwidth`: The total width to be used for the median indicator. It must be a number between 0 and 1. default: `1`
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `outlinecolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`). default: `:white`
  * `outlinethickness`: The mark outline thickness. default: `1`
  * `space`: The space between boxes. It must be a number between 0 and 1. default: `0.1`
  * `whiskercolor`: Specifiy the color for the whisker lines. default: `:black`
  * `whiskerdash`: Specifiy the dash style for the whisker lines. default: `[3, 3]`
  * `whiskerthickness`: Specifiy the thickness for the whisker lines. default: `1`

## Outliers appearance

  * `outliercolor`: Specifiy the color for the outliers symobls.
  * `outlierjitter`: Specifiy the jitter strength for the outliers symobls. default: `0`
  * `outlieropacity`: Specifiy the mark opacity for the outliers symobls. default: `1`
  * `outlieroutlinecolor`: Specifiy the outline color for the outliers symobls.
  * `outliersymbol`: Specifiy the symbol shape for the outliers symobls. default: `:circle`
  * `outliersymbolsize`: Specifiy the symbol size for the outliers symobls. default: `30`
  * `outlierthickness`: Specifiy the outline thickness for the outliers symobls. default: `1`

## BoxPlot tooltip

  * `tooltip`: A tooltip will be shown upon mouse hover. default: `false`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
