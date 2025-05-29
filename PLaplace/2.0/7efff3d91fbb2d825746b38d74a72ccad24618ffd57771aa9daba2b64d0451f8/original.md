```
assemble_derivativetensor(
    mesh::Mesh;
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}}
```

Returns the discrete derivative tensor for all elements of mesh and the number of components of the function qdim. Each key tuple (j,r) represents the derivative matrix for the component r in direction x_j.
