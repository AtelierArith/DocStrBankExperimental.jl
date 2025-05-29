```
has_edge(g::GNNHeteroGraph, edge_t, i, j)
```

Return `true` if there is an edge of type `edge_t` from node `i` to node `j` in `g`.

# Examples

```jldoctest
julia> g = rand_bipartite_heterograph((2, 2), (4, 0), bidirected=false)
GNNHeteroGraph:
  num_nodes: Dict(:A => 2, :B => 2)
  num_edges: Dict((:A, :to, :B) => 4, (:B, :to, :A) => 0)

julia> has_edge(g, (:A,:to,:B), 1, 1)
true

julia> has_edge(g, (:B,:to,:A), 1, 1)
false
```
