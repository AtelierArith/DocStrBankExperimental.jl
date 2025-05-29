```
TextPlot(args...)
```

Represent a Text plot with given arguments.

# Keyword arguments

## Required

  * `text`: The column to be used as text values for each point.
  * `x`: The column to be used as x coordinate.
  * `y`: The column to be used as y coordinate.

## TextPlot Options

  * `angleresponse`: The column which its values will be used to determine the angle of text.
  * `colorresponse`: The column which its values will be used to determine the color of text.
  * `opacityresponse`: The column which its values will be used to determine the opacity of text.

## Grouping

  * `group`: The name of column for grouping observation. Each group of observations will create seperate text plot.

## TextPlot appearance

  * `align`: The text alignment. default: `:left`
  * `angle`: The text angle. default: `0`
  * `color`: The text color. default: `:black`
  * `colormodel`: It specifies the color scheme to use for the marks. default: `:diverging`
  * `dir`: The direction of the text, i.e. `:ltr` or `:rtl`. default: `:ltr`
  * `font`: The font name for displaying text.
  * `fontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `italic`: If `true` the italic style will be used for displaying text.
  * `limit`: The maximum length of the text mark in pixels. The text value will be automatically truncated if the rendered size exceeds the limit.
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `size`: The font size for displaying text. default: `10`
  * `textbaseline`: The text baseline. default: `:alphabetic`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
