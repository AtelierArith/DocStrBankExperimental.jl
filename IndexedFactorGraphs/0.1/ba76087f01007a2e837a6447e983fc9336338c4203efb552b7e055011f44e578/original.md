```
IndexedGraphs.outedges(g::FactorGraph, v::FactorGraphVertex)
```

Return a lazy iterators to the edges incident on vertex `v`, with `v` as the source.

# Examples

```jldoctest outedges
julia> using IndexedFactorGraphs

julia> g = FactorGraph([0 1 1 0;
                        1 0 0 0;
                        0 0 1 1])
FactorGraph{Int64} with 4 variables, 3 factors, and 5 edges

julia> collect(outedges(g, factor(2)))
1-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 2 => 1 with index 1

julia> collect(outedges(g, variable(3)))
2-element Vector{IndexedGraphs.IndexedEdge{Int64}}:
 Indexed Edge 3 => 1 with index 3
 Indexed Edge 3 => 3 with index 4
```
