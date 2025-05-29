```
assemble_laplacian(
    D::SparseMatrixCSC{Float64, Int64},
    w::AbstractVector{Float64}
) -> SparseMatrixCSC{Float64, Int64}
```

Returns the Laplacian stiffness matrix for all elements of a mesh and qdim components.

Takes existing derivative matrix D and weight vector w as arguments. Can yield performance benefits compared to direct assembly if D already exists. Note that number of components and quadrature order in D and w have to match.
