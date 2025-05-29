```
Legend(args...)
```

Represent a Legend with given arguments.

# Keyword arguments

## Legend identity

  * `name`: The legend id which refers to a legend id of a plot.

## Legend options

  * `d3format`: Allow users to directly pass a legend format. It must follow the rules described in `d3.format()`.
  * `d3formattype`: If values are time or date, this option can be used to control their format.
  * `limit`: The number of elements to be shown in the legend.
  * `values`: Allow user manually provide the values for the legend.

## Legend appearance

  * `columns`: The number of columns to be used to show the legend elements. default: `1`
  * `columnspace`: The space between columns. default: `1`
  * `direction`: The direction of the legend. default: `:vertical`
  * `font`: The default font that will be used for all elements of the legend.
  * `fontweight`: The default font weight that will be used for all elements of the legend.
  * `gradientlength`: Control the size of a gradient type legend.
  * `gradientthickness`: Control the size of a gradient type legend (width).
  * `gridalign`: Control how to align multiple legends. default: `:each`
  * `italic`: The default font style that will be used for all elements of the legend.
  * `orient`: The location of the legend. User can pass `[legendX, legendY]` for a precise location. default: `:right`
  * `rowspace`: The space between rows. default: `1`
  * `size`: The legend element size. default: `100`
  * `symbol`: Indicate the symbol for discrete type legends.

## Title properties

  * `title`: Legend title.
  * `titlefont`: The font name for displaying text.
  * `titlefontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `titleitalic`: If `true` the italic style will be used for displaying text.
  * `titlesize`: The font size for displaying text.

## Labels properties

  * `labelfont`: The font name for displaying text.
  * `labelfontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `labelitalic`: If `true` the italic style will be used for displaying text.
  * `labelsize`: The font size for displaying text.
