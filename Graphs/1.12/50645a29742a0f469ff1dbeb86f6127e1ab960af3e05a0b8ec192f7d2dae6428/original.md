```
transitivereduction(g; selflooped=false)
```

Compute the transitive reduction of  a directed graph. If the graph contains cycles, each strongly connected component is replaced by a directed cycle and the transitive reduction is calculated on the condensation graph connecting the components. If `selflooped` is true, self loops on strongly connected components of size one will be preserved.

### Performance

Time complexity is $\mathcal{O}(|V||E|)$.

# Examples

```jldoctest
julia> using Graphs

julia> barbell = blockdiag(complete_digraph(3), complete_digraph(3));

julia> add_edge!(barbell, 1, 4);

julia> collect(edges(barbell))
13-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
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

julia> collect(edges(transitivereduction(barbell)))
7-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 4
 Edge 2 => 3
 Edge 3 => 1
 Edge 4 => 5
 Edge 5 => 6
 Edge 6 => 4
```
