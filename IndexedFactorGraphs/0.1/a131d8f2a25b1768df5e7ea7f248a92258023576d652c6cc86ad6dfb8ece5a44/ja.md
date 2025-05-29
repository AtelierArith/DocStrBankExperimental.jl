```
IndexedGraphs.inedges(g::FactorGraph, v::FactorGraphVertex)
```

頂点 `v` に接続されたエッジへの遅延イテレータを返します。`v` は宛先です。

# 例

```jldoctest inedges
julia> using IndexedFactorGraphs

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} は 4 つの変数、3 つの因子、5 つのエッジを持っています

julia> collect(inedges(g, factor(2)))
1-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 1 => 2 with index 1


julia> collect(inedges(g, variable(3)))
2-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 1 => 3 with index 3
 Indexed Edge 3 => 3 with index 4
```
