```
write_to_txt(
    x::Vector{Float64},
    mesh::Mesh,
    file_name::String;
    qdim::Int64 = 1
)
```

Writes a coefficient vector x with qdim components based on the nodes of mesh to the given file.
