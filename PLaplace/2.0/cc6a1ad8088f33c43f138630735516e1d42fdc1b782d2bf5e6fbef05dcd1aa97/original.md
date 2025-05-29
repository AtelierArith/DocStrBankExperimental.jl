```
assemble_derviativetensor_modified(
    D::AbstractDict{Tuple{Int64,Int64},SparseMatrixCSC{Float64,Int64}},
    nodesToDrop::Set{Int64};
    qdim::Int64 = 1
) -> Dict{Tuple{Int64, Int64}, SparseArrays.SparseMatrixCSC{Float64, Int64}}
```

Returns a new derivative tensor reduced by nodesToDrop, e.g used to drop homogeneous Dirichtlet boundary points of the mesh.
