```
write_to_vtk_boundary(
    x::Vector{Vector{Float64}},
    mesh::Mesh, 
    data_names::Array{String}, 
    file_name::String, 
    qdim::Array{Int64};
    boundary=Set{Boundary}()
)
```

Writes multiple data vectors with corresponding names and qdims based on the boundary elements of the mesh to a .vtk-file with the given name.
