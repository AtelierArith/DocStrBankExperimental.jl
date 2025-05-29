```julia
assemble_elasticity(
    mesh::MinFEM.Mesh,
    lambda::Float64,
    mu::Float64
) -> SparseArrays.SparseMatrixCSC{Float64, Int64}

```

Returns the linear elasticity stiffness matrix with constant coefficients λ and μ  for all elements of mesh and image dimension qdim.
