```julia
elementdiameter(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Union{Float64, Int64}

```

前の `elementdiameter(...)` と同様ですが、メッシュと要素IDを引数として受け取ります。メッシュからサポートノードの座標を抽出し、それらを基底関数に渡します。
