```
IndexedGraphs.outedges(g::FactorGraph, v::FactorGraphVertex)
```

頂点 `v` に接続されたエッジへの遅延イテレータを返します。`v` はソースとして扱われます。

# 例

```jldoctest outedges
julia> using IndexedFactorGraphs

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} は 4 つの変数、3 つの因子、および 5 つのエッジを持っています

julia> collect(outedges(g, factor(2)))
1-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 2 => 1 with index 1

julia> collect(outedges(g, variable(3)))
2-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 3 => 1 with index 3
 Indexed Edge 3 => 3 with index 4
```
