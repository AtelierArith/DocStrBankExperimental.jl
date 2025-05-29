```
outernormalvector(
    mesh::Mesh;
    boundaryElements::Set{Int64} = Set{Int64}()
) -> Vector{Float64}
```

Returns coefficient vector of outer normal vectors at all or specified boundary elements of the given mesh.
