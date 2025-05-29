```julia
elementdiameter_boundary(
    coords::Vector{Vector{Float64}}
) -> Union{Float64, Int64}

```

与えられた座標でスパンされた境界要素の直径（すなわち、最長辺の長さ）を返します。

一般的に、座標はメッシュ内の1つの境界要素に対応しますが、必ずしもそうである必要はありません。

要素をスパンするノードの数は指定されていないため、機能は `elementdiameter(args)` と同じです。ただし、この関数は一貫性と可読性の向上のために保持されています。
