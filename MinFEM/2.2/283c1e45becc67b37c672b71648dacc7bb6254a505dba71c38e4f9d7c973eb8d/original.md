```
write_to_vtk(
    x::Vector{Vector{Float64}},
    mesh::Mesh,
    data_names::Array{String}, 
    file_name::String;
    qdim::Int64 = 1
)
```

Same as pervious `write_to_vtk(...)`, but can handles simplification by submitting one qdim for all data vectors if they are the same. If everything is scalar no specification of qdim is required. 
