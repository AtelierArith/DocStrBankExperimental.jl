```
evaluate_mesh_function(
    mesh::Mesh,
    f::Function,
    region::Set{Boundary};
    qdim::Int64 = 1
) -> Vector{Float64}
```

Returns evaluation of a given function object f on all or specified nodes of the mesh. Can be either called with set of physical boundaries or directly with a set of nodes  when given with keyword argument region.
