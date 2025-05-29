```
ArrayShape{N}
```

is the type of eligible argument to represent an `N`-dimensional array shape as usually accepted in Julia: it is an `N`-tuple of integers and/or integer-valued unit ranges.

Methods [`as_array_shape`](@ref), [`as_array_axes`](@ref), and [`as_array_size`](@ref) may be called on any `ArrayShape{N}` instance to convert it to a canonical form of array axes or size.

Expression `eltype(ArrayShape)` yields the union of possible types for each entry of an array shape. This may be used to specify a variable number of arguments possibly representing an array shape.

See also [`ArrayAxes`](@ref), `Dims`.
