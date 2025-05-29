```
bridges(g)
```

Compute the [bridges](https://en.m.wikipedia.org/wiki/Bridge_(graph_theory)) of a connected graph `g` and return an array containing all bridges, i.e edges whose deletion increases the number of connected components of the graph.

# Examples

```jldoctest
julia> using LightGraphs

julia> bridges(star_graph(5))
8-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 1 => 5

julia> bridges(path_graph(5))
8-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 4 => 5
 Edge 3 => 4
 Edge 2 => 3
 Edge 1 => 2
```
