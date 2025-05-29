```julia
jacobian_boundary(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Union{Nothing, Float64, Int64}

```

前の `jacobian_boundary(...)` と同様ですが、メッシュと要素IDを引数として受け取ります。メッシュからサポートノードの座標を抽出し、それを基本関数に渡します。
