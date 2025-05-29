```
V_motifs(G::Graphs.SimpleGraph; membership::Vector=Graphs.bipartite_map(G), layer::Symbol=:bottom)
```

Count the total number of V-motif occurences in graph `G` for one of its layers.

*Note*: the bipartiteness of the graph is not explicitely checked.

# Arguments

  * `membership`: the bipartite mapping of the graphs. This can be computed using `Graphs.bipartite_map(G)`.
  * `layer`: the layer can be specified by passing `layer=:bottom` or `layer=:top`. Layer membership is determined by the bipartite map of the graph.

# Examples

```jldoctest V_motifs_bipartite
julia> using Graphs

julia> G = SimpleGraph(5); add_edge!(G, 1, 4); add_edge!(G, 2, 4); add_edge!(G, 3, 4); add_edge!(G, 3, 5);

julia> V_motifs(G, layer=:bottom)
3

```

```jldoctest V_motifs_bipartite
julia> V_motifs(G, layer=:top)
1

```
