```julia
elementdiameter_boundary(
    mesh::MinFEM.Mesh,
    nodes::Vector{Int64}
) -> Union{Float64, Int64}

```

前の `elementdiameter_boundary(...)` と同様ですが、メッシュとノードのセットを引数として取ります。メッシュから座標を抽出し、それを基本関数に渡します。

一般的に、座標はメッシュ内の1つの（境界）要素に対応しますが、必ずしもそうである必要はありません。

要素を構成するノードの数は指定されていないため、機能は `elementdiameter(args)` と同じです。しかし、この関数は一貫性と可読性の向上のために保持されています。
