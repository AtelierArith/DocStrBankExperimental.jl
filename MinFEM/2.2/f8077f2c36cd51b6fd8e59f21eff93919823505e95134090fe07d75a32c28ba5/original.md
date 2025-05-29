```julia
jacobian(
    coords::Vector{Vector{Float64}}
) -> Tuple{Float64, LinearAlgebra.Adjoint{Float64, Matrix{Float64}}}

```

Returns determinant (i.e. element weight) and inverse transposed of the jacobian  of an FEM element spanned by nodes at the given coordinates.

Commonly the coordinates correspond to one element in a mesh, but not necessarily have to.
