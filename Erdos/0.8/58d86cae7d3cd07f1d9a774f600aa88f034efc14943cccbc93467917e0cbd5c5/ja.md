```
mutable struct Graph{T<:Integer} <: AGraph
    ne::Int
    fadjlist::Vector{Vector{T}}
end
```

隣接リストに基づく単純グラフ型。

コンストラクタ

```
Graph{T}(n=0)
Graph(n=0) = Graph{Int}(n)
```

`n` 頂点とエッジのない `Graph` を返します。

```
Graph{T}(adjmx::AbstractMatrix; upper=false, selfedges=true)
```

隣接行列 `adjmx` から `Graph{T}` を構築し、`adjmx` の各非ゼロ要素に対応するエッジを配置します。`selfedges=false` の場合、`adjmx` の対角要素は無視されます。`upper=true` の場合、`adjmx` の上三角部分のみが考慮されます。
