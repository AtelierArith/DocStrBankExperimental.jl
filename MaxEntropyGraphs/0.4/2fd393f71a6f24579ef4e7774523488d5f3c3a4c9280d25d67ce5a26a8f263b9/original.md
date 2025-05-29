```
V_motifs(G::Graphs.SimpleGraph, i::Int, j::Int; membership::Vector=Graphs.bipartite_map(G))
```

Count the number of V-motif occurences in graph `G` between nodes `i` and `j` of the graph.

*Notes*: 

1. the bipartiteness of the graph is not explicitely checked.
2. this uses the actual node numbers in the graph, not their numbering in the specific layer.

# Arguments

  * `membership`: the bipartite mapping of the graphs. This can be computed using `Graphs.bipartite_map(G)`.

# Examples

```jldoctest V_motifs_nodes
julia> using Graphs

julia> G = SimpleGraph(5); add_edge!(G, 1, 4); add_edge!(G, 1, 5); add_edge!(G, 2, 4); add_edge!(G, 2, 5); add_edge!(G, 3, 4);

julia> V_motifs(G, 1, 2)
2

```
