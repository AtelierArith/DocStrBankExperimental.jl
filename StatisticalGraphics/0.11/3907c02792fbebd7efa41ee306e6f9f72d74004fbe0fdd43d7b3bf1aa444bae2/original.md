```
Bar(args...)
```

Represent a Bar chart with given arguments.

# Keyword arguments

## Required

  * `x`: User should pass a single column for plotting the bar chart. User must pass either this or the `y` argument. default: `0`
  * `y`: User should pass a single column for plotting the bar chart. User must pass either this or the `x` argument. default: `0`

## Bar options

  * `baseline`: The start value for drawing bars. default: `0`
  * `baselineresponse`: Name/index of a numeric column which will be used to change the baseline of bars within each group. The function passed to `baselinestat` will be used to aggregate the values if there are more than one observation for a specific bar.
  * `baselinestat`: The function that will be used to aggregate values in column passed as `baselineresponse`.
  * `colormodel`: It specifies the color scheme to use for the marks. default: `:diverging`
  * `colorresponse`: Name/index of a numeric column which will be used to change the fill color of each bar based on its values. The function passed to `colorstat` will be used to aggregate the values if there are more than one observation for a specific bar.
  * `colorstat`: The function that will be used to aggregate values in column passed as `colorresponse`.
  * `missingmode`: Indicate how to handle missing values in category or group.  `0` = nothing, `1` = no missing in category, `2` = no missing in group, `3` = no missing in category or group, `4` = no missing in category and group. default: `0`
  * `normalize`: If `true` the bars will be normalized in each group. By default the total bar heights will be `1` in each group, however, user can pass customised function via `normalizer` to change this behaviour. default: `false`
  * `normalizer`: This function will be used to normalize bar height within each group. default: `StatisticalGraphics.bar_normalizer`
  * `orderresponse`: Name of a numeric column which will be used to change the order of bars. The function passed to `orderstat` will be used to aggregate the values if there are more than one observation for a specific bar. Note that the axis' order will override this.
  * `orderstat`: The function that will be used to aggregate values in column passed as `orderresponse`.
  * `response`: A numeric column which its aggregated values based on the `stat` keyword argument will be used to determine the height of each bar.
  * `stat`: A function for aggregating the `response` keyword argument. When `response` is passed the default value of the keword change to `IMD.sum`, however, user can pass any function to this argument. The function must accept two arguments `f`(format), and `x` the input values and return the aggregated values.

## Grouping

  * `group`: A grouped bar chart will be created by passing a single column to this argument.
  * `groupdisplay`: Indicate how to display bars in each group. It can be `:stack`, `:cluster`, `:step`, or `:none`. default: `:stack`
  * `grouporder`: How to order values in each group. It can be `:data`, `:ascending`, or `:descending`. User may also pass a vector of group levels to dictate the orders. default: `:ascending`
  * `groupspace`: The space between bars inside each group when `groupdisplay` is in (`:cluster`, `:step`). default: `0.05`

## Bar appearance

  * `barcorner`: Corner radius for bars. (`cornerRadiusTopLeft`, `cornerRadiusTopRight`, `cornerRadiusBottomLeft`, `cornerRadiusBottomRight`). default: `0`
  * `barwidth`: The bar width proportion with respect to the available space. It can be any number between 0 and 1. User can pass `:nest` too, which in this case the bar width will be automatically calculated for each group in such a way that the bar widths in each group will be smaller than the previous group. Users can pass `nestfactor` to control how fast they would like the bar width change for each group. default: `1`
  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `"#4682b4"`
  * `nestfactor`: When the `barwidth` keyword is set to `:nest` this will control how much change should be applied to the current group barwidth compared to the previous one. By default this will be controlled automatically.
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `outlinecolor`: The mark's outline color. default: `:white`
  * `outlinethickness`: The mark outline thickness. default: `1`
  * `space`: The space between bars. It can be any number between 0 and 1.  default: `0.1`

## Bar labels

  * `label`: What information should be used for bar labels. It can be `:none`, `:height`, or `:category`. default: `:none`
  * `labelalign`: The text alignment.
  * `labelalternate`: Use automatic alogirhtms to adjust the labels for bar with negative heights. default: `true`
  * `labelangle`: The text angle.
  * `labelbaseline`: The text baseline.
  * `labelcolor`: The text color. User can also pass `:group` or `:colorresponse` to use the corresponding scale for coloring the text. default: `:black`
  * `labeld3format`: d3 format for labels. default: `""`
  * `labeldir`: The direction of the text, i.e. `:ltr` or `:rtl`. default: `:ltr`
  * `labelfont`: The font name for displaying text.
  * `labelfontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `labelitalic`: If `true` the italic style will be used for displaying text.
  * `labellimit`: The maximum length of the text mark in pixels. The text value will be automatically truncated if the rendered size exceeds the limit.
  * `labelloc`: relative location of the label within each bar. It can be any number between 0 and 1, where 0.5 means middle of the bar. default: `0.5`
  * `labeloffset`: The amount in pixel to offset the labels. default: `0`
  * `labelopacity`: The text opacity. default: `1`
  * `labelpos`: The position of labels within each bar. It can be `:end`, `:start`, or `:middle`. default: `:end`
  * `labelsize`: The font size for displaying text.
  * `tooltip`: A tooltip will be shown upon mouse hover. default: `false`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
