```julia
assemble_massmatrix(
    E::SparseArrays.SparseMatrixCSC{Float64, Int64},
    w::AbstractVector{Float64}
) -> SparseArrays.SparseMatrixCSC{Float64, Int64}

```

Returns the mass matrix with given local integration order for all elements  of mesh and qdim components.

Takes existing basis matrix E and weight vector w as arguments. Can yield performance benefits compared to direct assembly if E already exists. Note that number of components and quadrature order in E and w have to match.
