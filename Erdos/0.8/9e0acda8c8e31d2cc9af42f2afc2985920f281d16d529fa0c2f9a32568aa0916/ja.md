```
mutable struct DiGraph{T<:Integer} <: ADiGraph
    ne::Int
    fadjlist::Vector{Vector{T}}
    badjlist::Vector{Vector{T}}
end
```

2つの隣接リスト（前方と後方）に基づくシンプルな有向グラフタイプ。

```
DiGraph{T}(n=0)
DiGraph(n=0) = DiGraph{Int}(n)
```

`n` 頂点とエッジのない `DiGraph` を構築します。

```
DiGraph{T}(adjmx::AbstractMatrix; selfedges=true)
```

隣接行列 `adjmx` から `DiGraph{T}` を構築し、`adjmx` の各非ゼロ要素に対応するエッジを配置します。`selfedges=false` の場合、`adjmx` の対角要素は無視されます。
