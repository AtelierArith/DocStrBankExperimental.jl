```julia
elementdiameter_boundary(
    coords::Vector{Vector{Float64}}
) -> Union{Float64, Int64}

```

Returns diameter (i.e. longest edge length) of a boundary element spanned by nodes at the given coordinates.

Commonly the coordinates correspond to one boundary element in a mesh, but not necessarily have to.

Since the number of nodes to span an element is not prescribed, the functionality is identical to `elementdiameter(args)`. However this function is kept for consistency and improved readability.
