```
write_to_vtk_boundary(
    x::Vector{Float64},
    mesh::Mesh, 
    data_name::String,
    file_name::String; 
    boundary = Set{Boundary}(),
    qdim::Int64 = 1
)
```

Same as pervious `write_to_vtk_boundary(...)`, but handles setting for a single data vector with corresponding name and qdim. Forwards them to base implementation as array with one entry.
