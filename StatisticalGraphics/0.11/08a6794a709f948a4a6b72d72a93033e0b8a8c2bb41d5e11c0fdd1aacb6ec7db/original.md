```
Bubble(args...)
```

Represent a Bubble plot with given arguments.

# Keyword arguments

## Required

  * `x`: The column to be used as x coordinate. default: `0`
  * `y`: The column to be used as y coordinate. default: `0`

## Bubble Options

  * `colorresponse`: The column which its values will be used to determine the fill color of the marks.
  * `maxsize`: The maximum size of the bubbles.
  * `minsize`: The minimum size of the bubbles.
  * `opacityresponse`: The column which its values will be used to determine the opacity of the marks.

## Grouping

  * `group`: The name of column for grouping observation. Each group of observations will create seperate bubble plot.

## Bubble appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`).
  * `colormodel`: It specifies the color scheme to use for the marks. default: `:diverging`
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `outlinecolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`).
  * `size`: The symbol size. default: `50`
  * `thickness`: The mark outline thickness. default: `1`

## Bubble Label

  * `labelalgorithm`: The algorithm for placing labels. default: `:naive`
  * `labelanchor`: The anchors for choosing the location of labels. default: `[:top, :bottom, :left, :right]`
  * `labelangle`: The text angle. default: `0`
  * `labelcolor`: The label text color, it can also be `:group` or `:colorresponse` for choosing the color based on the points groups. default: `:black`
  * `labeldir`: The direction of the text, i.e. `:ltr` or `:rtl`. default: `:ltr`
  * `labelfont`: The font name for displaying text.
  * `labelfontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `labelitalic`: If `true` the italic style will be used for displaying text.
  * `labellimit`: The maximum length of the text mark in pixels. The text value will be automatically truncated if the rendered size exceeds the limit.
  * `labelresponse`: The column which its values will be used to label points.
  * `labelsize`: The font size for displaying text.
  * `tooltip`: A tooltip will be shown upon mouse hover. default: `false`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `xshift`: Shift the mark in direction of x. Useful for discrete type axes. default: `0`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`
  * `yshift`: Shift the mark in direction of y. Useful for discrete type axes. default: `0`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
