```julia
stem(; y, stem_color, stem_thickness, kwargs...)

```

Creates a "stem" or "lollipop" trace. It is implemented using plotly.js's `scatter` type, using the error bars to draw the stem.

## Keyword Arguments:

  * All properties accepted by `scatter` except `error_y`, which is used to draw   the stems
  * stem_color - sets the color of the stems
  * stem_thickness - sets the thickness of the stems
