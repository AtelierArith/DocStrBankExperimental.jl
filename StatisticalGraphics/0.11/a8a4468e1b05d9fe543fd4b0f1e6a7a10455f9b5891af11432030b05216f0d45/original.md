```
Pie(args...)
```

Represent a Pie chart with given arguments.

# Keyword arguments

## Required

  * `category`: A category column which indicates each slice. default: `0`

## Pie options

  * `endangle`: The end angle in degree. default: `360`
  * `missingmode`: Indicate how to handle missing values in category or group.  `0` = nothing, `1` = no missing in category, `2` = no missing in group, `3` = no missing in category or group, `4` = no missing in category and group. default: `0`
  * `response`: A numeric column which its aggregated values based on the `stat` keyword argument will be used to determine the radius of each slice.
  * `sort`: If `true` the slices will be sorted based on their total angle. default: `false`
  * `startangle`: The start angle in degree. default: `0`
  * `stat`: A function for aggregating the `response` keyword argument. When `response` is passed the default value of the keword change to `IMD.sum`, however, user can pass any function to this argument. The function must accept two arguments `f`(format), and `x` the input values and return the aggregated values.

## Grouping

  * `group`: A nested pie chart will be created by passing a single column to this argument.
  * `groupspace`: The space between nested pie. default: `0.01`

## Pie appearance

  * `colormodel`: It specifies the color scheme to use for the marks. default: `:category`
  * `innerradius`: The donut radius. It must be a number between 0 and 1. default: `0`
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `outerradius`: The outer radius. It must be a number between 0 and 1. default: `1`
  * `outlinecolor`: The mark's outline color. default: `:white`
  * `outlinethickness`: The mark outline thickness. default: `1`
  * `piecorner`: The corner of slice in pixel. default: `0`
  * `space`: The space between slices. It can be any number between 0 and 1.  default: `0`

## Pie labels

  * `decimal`: Numbe of digits after the decimal when percentage is used. default: `1`
  * `label`: What information should be used for slice labels. It can be `:category`, `:percent`, or `:both`.
  * `labelalign`: The text alignment. default: `:center`
  * `labelangle`: The text angle.
  * `labelbaseline`: The text baseline. default: `:middle`
  * `labelcolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`). default: `:black`
  * `labeldir`: The direction of the text, i.e. `:ltr` or `:rtl`. default: `:ltr`
  * `labelfont`: The font name for displaying text.
  * `labelfontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `labelitalic`: If `true` the italic style will be used for displaying text.
  * `labellimit`: The maximum length of the text mark in pixels. The text value will be automatically truncated if the rendered size exceeds the limit.
  * `labelopacity`: The text opacity. default: `1`
  * `labelpos`: Vertical position of lables. default: `0.5`
  * `labelrotate`: It rotates text 90 degree. default: `false`
  * `labelsize`: The font size for displaying text.
  * `labelthreshold`: Labels will be drop for the slices with smaller angle than `:labelthreshold`. default: `0.0`
  * `tooltip`: A tooltip will be shown upon mouse hover. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
