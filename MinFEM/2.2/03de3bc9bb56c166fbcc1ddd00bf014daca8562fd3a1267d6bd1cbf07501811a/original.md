```julia
jacobian_boundary(
    coords::Vector{Vector{Float64}}
) -> Union{Nothing, Float64, Int64}

```

Returns determinant of the jacobian (i.e. element weight) of an FEM boundary element (in d-1 dimensions) spanned spanned by nodes at the given coordinates.

Commonly the coordinates correspond to an element in a mesh, but not necessarily have to.
