```
write_to_vtk(
    x::Vector{Float64},
    mesh::Mesh,
    data_name::String, 
    file_name::String;
    qdim::Int64 = 1
)
```

Same as pervious `write_to_vtk(...)`, but handles setting for a single data vector with corresponding name and qdim. Forwards them to base implementation as array with one entry.
