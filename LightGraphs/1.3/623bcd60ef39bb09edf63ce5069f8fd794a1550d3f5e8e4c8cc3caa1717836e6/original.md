```
condensation(g[, scc])
```

Return the condensation graph of the strongly connected components `scc` in the directed graph `g`. If `scc` is missing, generate the strongly connected components first.

# Examples

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0])
{5, 6} directed simple Int64 graph

julia> strongly_connected_components(g)
2-element Array{Array{Int64,1},1}:
 [4, 5]
 [1, 2, 3]

julia> foreach(println, edges(condensation(g)))
Edge 2 => 1
```
