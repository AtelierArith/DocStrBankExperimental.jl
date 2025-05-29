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

前の `write_to_vtk_boundary(...)` と同様ですが、すべてのデータベクトルが同じであれば、すべてのデータベクトルに対して1つの qdim を提出することで簡略化を処理できます。すべてがスカラーの場合、qdim の指定は必要ありません。
