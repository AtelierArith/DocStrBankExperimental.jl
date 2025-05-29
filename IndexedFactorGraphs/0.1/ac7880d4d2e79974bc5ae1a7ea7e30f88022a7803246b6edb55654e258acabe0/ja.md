```
IndexedGraphs.neighbors(g::FactorGraph, v::FactorGraphVertex)
```

頂点 `v` の隣接点への遅延イテレータを返します。

# 例

```jldoctest neighbors
julia> using IndexedFactorGraphs

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} with 4 variables, 3 factors, and 5 edges

julia> collect(neighbors(g, variable(3)))
2-element Vector{Int64}:
 1
 3

julia> collect(neighbors(g, factor(2)))
1-element Vector{Int64}:
 1
```
