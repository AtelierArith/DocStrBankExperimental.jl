```
write_to_vtk(
    x::Vector{Vector{Float64}},
    mesh::Mesh,
    data_names::Array{String}, 
    file_name::String,
    qdim::Array{Int64}
)
```

Writes multiple data vectors with corresponding names and qdims to a .vtk-file with the given name.
