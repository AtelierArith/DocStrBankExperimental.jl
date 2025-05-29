```
series(curves)
```

Curves can be:

  * `AbstractVector{<: AbstractVector{<: Point2}}`: the native representation of a series as a vector of lines
  * `AbstractMatrix`: each row represents y coordinates of the line, while `x` goes from `1:size(curves, 1)`
  * `AbstractVector, AbstractMatrix`: the same as the above, but the first argument sets the x values for all lines
  * `AbstractVector{<: Tuple{X<: AbstractVector, Y<: AbstractVector}}`: A vector of tuples, where each tuple contains a vector for the x and y coordinates

If any of `marker`, `markersize`, `markercolor`, `strokecolor` or `strokewidth` is set != nothing, a scatterplot is added.

## Plot type

The plot type alias for the `series` function is `Series`.

## Attributes

**`color`** =  `:lighttest`  — *No docs available.*

**`joinstyle`** =  `@inherit joinstyle`  — *No docs available.*

**`labels`** =  `nothing`  — *No docs available.*

**`linecap`** =  `@inherit linecap`  — *No docs available.*

**`linestyle`** =  `:solid`  — *No docs available.*

**`linewidth`** =  `2`  — *No docs available.*

**`marker`** =  `nothing`  — *No docs available.*

**`markercolor`** =  `automatic`  — *No docs available.*

**`markersize`** =  `nothing`  — *No docs available.*

**`miter_limit`** =  `@inherit miter_limit`  — *No docs available.*

**`solid_color`** =  `nothing`  — *No docs available.*

**`space`** =  `:data`  — *No docs available.*

**`strokecolor`** =  `nothing`  — *No docs available.*

**`strokewidth`** =  `nothing`  — *No docs available.*
