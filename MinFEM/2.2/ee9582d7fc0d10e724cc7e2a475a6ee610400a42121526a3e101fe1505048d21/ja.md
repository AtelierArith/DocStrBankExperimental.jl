```julia
elementdiameter_boundary(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Union{Float64, Int64}

```

前の `elementdiameter_boundary(...)` と同様ですが、メッシュと境界要素IDを引数として受け取ります。メッシュからサポートノードの座標を抽出し、それを基本関数に渡します。
