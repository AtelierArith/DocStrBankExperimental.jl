```
bracket(x1, y1, x2, y2; kwargs...)
bracket(x1s, y1s, x2s, y2s; kwargs...)
bracket(point1, point2; kwargs...)
bracket(vec_of_point_tuples; kwargs...)
```

Draws a bracket between each pair of points (x1, y1) and (x2, y2) with a text label at the midpoint.

By default each label is rotated parallel to the line between the bracket points.

## Plot type

The plot type alias for the `bracket` function is `Bracket`.

## Attributes

**`align`** =  `(:center, :center)`  — *No docs available.*

**`color`** =  `@inherit linecolor`  — *No docs available.*

**`font`** =  `@inherit font`  — *No docs available.*

**`fontsize`** =  `@inherit fontsize`  — *No docs available.*

**`joinstyle`** =  `@inherit joinstyle`  — *No docs available.*

**`justification`** =  `automatic`  — *No docs available.*

**`linecap`** =  `@inherit linecap`  — *No docs available.*

**`linestyle`** =  `:solid`  — *No docs available.*

**`linewidth`** =  `@inherit linewidth`  — *No docs available.*

**`miter_limit`** =  `@inherit miter_limit`  — *No docs available.*

**`offset`** =  `0`  — The offset of the bracket perpendicular to the line from start to end point in screen units.     The direction depends on the `orientation` attribute.

**`orientation`** =  `:up`  — Which way the bracket extends relative to the line from start to end point. Can be `:up` or `:down`.

**`rotation`** =  `automatic`  — *No docs available.*

**`style`** =  `:curly`  — *No docs available.*

**`text`** =  `""`  — *No docs available.*

**`textcolor`** =  `@inherit textcolor`  — *No docs available.*

**`textoffset`** =  `automatic`  — *No docs available.*

**`width`** =  `15`  — The width of the bracket (perpendicularly away from the line from start to end point) in screen units.
