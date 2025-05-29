```
transitiveclosure(g, selflooped=false)
```

Compute the transitive closure of a directed graph, using DFS. Return a graph representing the transitive closure. If `selflooped` is `true`, add self loops to the graph.

### Performance

Time complexity is $\mathcal{O}(|E||V|)$.

# Examples

```jldoctest
julia> using LightGraphs

julia> barbell = blockdiag(complete_digraph(3), complete_digraph(3));

julia> add_edge!(barbell, 1, 4);

julia> collect(edges(barbell))
13-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 2 => 1
 Edge 2 => 3
 Edge 3 => 1
 Edge 3 => 2
 Edge 4 => 5
 Edge 4 => 6
 Edge 5 => 4
 Edge 5 => 6
 Edge 6 => 4
 Edge 6 => 5

julia> collect(edges(transitiveclosure(barbell)))
21-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 1 => 4
 Edge 1 => 5
 Edge 1 => 6
 Edge 2 => 1
 Edge 2 => 3
 Edge 2 => 4
 Edge 2 => 5
 Edge 2 => 6
 Edge 3 => 1
 Edge 3 => 2
 Edge 3 => 4
 Edge 3 => 5
 Edge 3 => 6
 Edge 4 => 5
 Edge 4 => 6
 Edge 5 => 4
 Edge 5 => 6
 Edge 6 => 4
 Edge 6 => 5
```
