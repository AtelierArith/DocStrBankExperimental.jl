```julia
elementdiameter(
    coords::Vector{Vector{Float64}}
) -> Union{Float64, Int64}

```

Returns diameter (i.e. longest edge length) of an element spanned by nodes at the given coordinates.

The coordinates do not necessarily have to span an element of full dimension. Could also be used for boundary elements.
