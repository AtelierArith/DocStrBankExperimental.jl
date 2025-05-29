```
write_to_vtk_boundary(
    x::Vector{Vector{Float64}},
    mesh::Mesh, 
    data_names::Array{String},
    file_name::String; 
    boundary = Set{Boundary}(),
    qdim::Int64 = 1
)
```

Same as pervious `write_to_vtk_boundary(...)`, but can handles simplification by submitting one qdim for all data vectors if they are the same. If everything is scalar no specification of qdim is required. 
