```
edges(g::FactorGraph)
```

Return a lazy iterator to the edges of `g`, with the convention that the source is the factor and the destination is the variable

```jldoctest edges
julia> using IndexedFactorGraphs

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} with 4 variables, 3 factors, and 5 edges

julia> collect(edges(g))
5-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 2 => 1 with index 1
 Indexed Edge 1 => 2 with index 2
 Indexed Edge 1 => 3 with index 3
 Indexed Edge 3 => 3 with index 4
 Indexed Edge 3 => 4 with index 5
```
