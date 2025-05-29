```
write_to_txt(
    x::Vector{Float64},
    mesh::Mesh,
    file_name::String;
    qdim::Int64 = 1
)
```

メッシュのノードに基づいて、qdim成分を持つ係数ベクトルxを指定されたファイルに書き込みます。
