```julia
elementdiameter(
    mesh::MinFEM.Mesh,
    nodes::Vector{Int64}
) -> Union{Float64, Int64}

```

前の `elementdiameter(...)` と同様ですが、メッシュとノードのセットを引数として取ります。メッシュから座標を抽出し、それを基本関数に渡します。

一般的に、座標はメッシュ内の1つの（境界）要素に対応しますが、必ずしもそうである必要はありません。
