```
Axis(args...)
```

Represent an Axis with given arguments.

# Keyword arguments

## Scale information

  * `exponent`: When `type=:power`, this will be used to pass the exponent.
  * `type`: The scale to be used for the axis, e.g. `:linear`, `:point`, `:band`, `:time`, `:date`, `:log`, `:symlog`, `:sqrt`, `:power`,... default: `:linear`

## Axis options

  * `d3format`: Allow users to directly pass an axis format. It must follow the rules described in `d3.format()`.
  * `d3formattype`: If values are time or date, this option can be used to control their format.
  * `dropmissing`: When `true` drops missings from discrete type axis domain. default: `false`
  * `nice`: Automatically round axis domain to make it nice. default: `true`
  * `offset`: The value to offset the axis. default: `1`
  * `order`: Determine how to order ticks for discrete types axis, e.g. `:data`, `:ascending`, `:descending`. default: `:data`
  * `padding`: Padding to extend axis. For discrete type axis it should be between 0 and 1, and for other type it indicates the amount in pixel.
  * `range`: Allow to manually set the domain of the axis.
  * `reverse`: Reverse the order of ticks. default: `false`
  * `show`: When it is `false`, `domain`, `title`, `ticks`, `labels` are set to `false`. default: `true`
  * `values`: User can use the keyword argument to manually put ticks. When a tuple of vector is passed, the first element will be used for the location and the second one will be used as displayed values.

## Grids

  * `grid`: Determine if the grids are shown. default: `false`
  * `gridcolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`). default: `:lightgray`
  * `griddash`: Grids dash style. default: `[0]`
  * `gridthickness`: Grids tickness. default: `0.5`

## Axis appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`). default: `:black`
  * `font`: The default font that will be used for all elements of the axis.
  * `fontweight`: The default font weight that will be used for all elements of the axis.
  * `italic`: The default font style that will be used for all elements of the axis.

## Domain properties

  * `domain`: If `false` the domain line would not be shown. default: `true`
  * `domaincolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`).
  * `domaindash`: The domain line dash. default: `[0]`
  * `domainthickness`: The domain line thickness. default: `1.01`

## Ticks properties

  * `tickcolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`).
  * `tickcount`: Number of ticks.
  * `tickdash`: Ticks dash style. default: `[0]`
  * `ticks`: If `false` the ticks will not be shown. default: `true`
  * `ticksize`: Ticks size in pixel. default: `5`
  * `tickthickness`: Tickness of ticks in pixel. default: `1.01`

## Title properties

  * `title`: Axis title.
  * `titlealign`: The text alignment.
  * `titleangle`: The text angle.
  * `titlebaseline`: The text baseline.
  * `titlecolor`: The text color.
  * `titlefont`: The font name for displaying text.
  * `titlefontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `titleitalic`: If `true` the italic style will be used for displaying text.
  * `titleloc`: Title location, i.e. `:middle`, `:end`, `:start`. default: `:middle`
  * `titlepadding`: Title padding.
  * `titlepos`: Title position in the form of [x,y].
  * `titlesize`: The font size for displaying text.

## Labels properties

  * `align`: The text alignment.
  * `angle`: The text angle. default: `0`
  * `baseline`: The text baseline.
  * `labelcolor`: The text color.
  * `labelfont`: The font name for displaying text.
  * `labelfontweight`: The font weight for displaying text, use 100 for thin font and 900 for the bold one.
  * `labelitalic`: If `true` the italic style will be used for displaying text.
  * `labeloverlap`: If `true`, avoids overlapping of labels. default: `true`
  * `labelpadding`: The extra padding between labels and ticks.
  * `labelsize`: The font size for displaying text.
  * `showlabels`: If `false` the axis labels will not be shown. default: `true`

## Miscellaneous

  * `translate`: The translate amount of the axis, see `vega` documentations for more information.
  * `zindex`: If `1` puts the axis elements on top of other marks in the graph. default: `0`
