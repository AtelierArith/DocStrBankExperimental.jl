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

前の `write_to_vtk_boundary(...)` と同様ですが、対応する名前と qdim を持つ単一のデータベクトルの設定を処理します。それらをエントリが1つの配列として基本実装に転送します。
