```
remove_nodes(g::GNNGraph, p)
```

Returns a new graph obtained by dropping nodes from `g` with independent probabilities `p`. 

# Examples

```julia
julia> g = GNNGraph([1, 1, 2, 2, 3, 4], [1, 2, 3, 1, 3, 1])
GNNGraph:
  num_nodes: 4
  num_edges: 6

julia> g_new = remove_nodes(g, 0.5)
GNNGraph:
  num_nodes: 2
  num_edges: 2
```
