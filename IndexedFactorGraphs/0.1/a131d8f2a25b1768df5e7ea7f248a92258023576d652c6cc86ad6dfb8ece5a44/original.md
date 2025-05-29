```
IndexedGraphs.inedges(g::FactorGraph, v::FactorGraphVertex)
```

Return a lazy iterators to the edges incident on vertex `v`, with `v` as the destination.

# Examples

```jldoctest inedges
julia> using IndexedFactorGraphs

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} with 4 variables, 3 factors, and 5 edges

julia> collect(inedges(g, factor(2)))
1-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 1 => 2 with index 1


julia> collect(inedges(g, variable(3)))
2-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 1 => 3 with index 3
 Indexed Edge 3 => 3 with index 4
```
