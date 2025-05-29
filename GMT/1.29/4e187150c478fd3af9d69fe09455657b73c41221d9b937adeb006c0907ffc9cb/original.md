```
setcoords!(GI::GItype; x::Vector{<:Real}=Float64[], y::Vector{<:Real}=Float64[], registration::Int=0)
```

Assign x,y coordinates to a GMTgrid or GMTimage. The `x,y` arguments are mandatory and can be two elements vectors with [xmin, xmax] and [ymin, ymax] respectively or vectors with ncolumns and nrows if `registration=0` or with ncolumns+1 and nrows+1 if `registration=1`.

### Return

This function returns nothing as what it does is to change the object coordinates information. See also the `setsrs!` function.
