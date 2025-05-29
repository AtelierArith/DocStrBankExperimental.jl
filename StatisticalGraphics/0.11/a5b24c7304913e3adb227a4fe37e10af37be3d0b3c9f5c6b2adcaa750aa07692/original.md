```
Polygon(args...)
```

Represent a Polygon with given arguments.

# Keyword arguments

## Required

  * `id`: The function draw a seperate polygon for each unique value of `id`.
  * `x`: The x coordinate of the polygon.
  * `y`: The y coordinate of the polygon.

## Polygon Options

  * `colorresponse`: The column which its values will be used to determine the fill color of polygons.
  * `interpolate`: The interplate function to use for drawing lines, e.g. `:linear`, `:basis`, `:natural`, `:step`, ... default: `:linear`
  * `opacityresponse`: The column which its values will be used to determine the opacity of polygons.
  * `outline`: If `true` an outline will be drawn for each polygon. default: `true`

## Grouping

  * `group`: The name of column for grouping observation. Each group of observations will create seperate polygon and polygons in each group will have different color.

## Polygon appearance

  * `color`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `:steelblue`
  * `colormodel`: The color model which will be used for fill color when `colorresponse` is passed. It can be an scheme or a vector of colors. default: `:diverging`
  * `opacity`: The mark opacity from 0 (transparent) to 1 (opaque). default: `1`
  * `outlinecolor`: The default color for the mark. User can pass color's name as symbol (e.g. `:red`), as string (e.g. `"red"`), as HTML color value (e.g. `"#4682b4"`), or pass a gradient color using the `gradient()` function. default: `:steelblue`
  * `outlinedash`: The outline dash style. default: `[0]`
  * `outlineopacity`: The ouline opacity. default: `1`
  * `outlinethickness`: The outline thickness. default: `1`

## Axes options

  * `x2axis`: When set to `true`, the top x-axis will be used for the current plot. default: `false`
  * `y2axis`: When set to `true`, the right y-axis will be used for the current plot. default: `false`

## Legend

  * `legend`: User can pass a symbol to this keyword argument to indicate that more customisation will be passed for the legened of corresponding mark. User needs to provide the extra customisation via the `Legend` global keyword.

## Miscellaneous

  * `clip`: Indicates if the marks should be clipped.
