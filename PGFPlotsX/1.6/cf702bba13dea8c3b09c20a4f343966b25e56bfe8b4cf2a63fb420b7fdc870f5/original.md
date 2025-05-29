```julia
Coordinate(data; error, errorplus, errorminus, meta)

```

Construct a coordinate, with optional error bars and metadata. `data` should be a 2- or 3-element tuples of finite real numbers.

You can specify *either*

1. `error`, which will then be used for error bars in both directions, or
2. `errorplus` and/or `errorminus`, for asymmetrical error bars.

Error values can be tuples of the same kind as `data`, or `nothing`.

Metadata can be provided in `meta`.

Users rarely need to use this constructor, see methods of [`Coordinates`](@ref) for constructing coordinates from arrays.
