```
assemble_derivativetensor_boundary(
    mesh::Mesh,
    BoundaryElements::Set{Int64}; 
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}}
```

Returns the discrete derivative tensor for all or specified boundary elements of mesh and number of components qdim. Each key tuple (j,r) represents the derivative matrix for the component r in direction x_j. Workaround based on the derivate tensor for the corresponding full element and the fact that the gradient is constant on the element. 
