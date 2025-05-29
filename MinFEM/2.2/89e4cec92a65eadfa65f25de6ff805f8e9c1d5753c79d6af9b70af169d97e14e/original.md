```
assemble_weightmultivector_boundary(
    mesh::Mesh;
    qdim::Int64 = 1,
    order::Int64 = 1
) -> Vector{Float64}
```

Returns the vector of weights for all boundary elements of mesh and qdim components. Weight is equal to volume if 1st order integration by mid-point rule is used.
