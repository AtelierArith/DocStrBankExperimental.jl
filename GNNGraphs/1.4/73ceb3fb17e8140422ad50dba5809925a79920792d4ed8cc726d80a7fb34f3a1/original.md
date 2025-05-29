```
perturb_edges([rng], g::GNNGraph, perturb_ratio)
```

Return a new graph obtained from `g` by adding random edges, based on a specified `perturb_ratio`.  The `perturb_ratio` determines the fraction of new edges to add relative to the current number of edges in the graph.  These new edges are added without creating self-loops. 

The function returns a new `GNNGraph` instance that shares some of the underlying data with `g` but includes the additional edges.  The nodes for the new edges are selected randomly, and no edge data (`edata`) or weights (`w`) are assigned to these new edges.

# Arguments

  * `g::GNNGraph`: The graph to be perturbed.
  * `perturb_ratio`: The ratio of the number of new edges to add relative to the current number of edges in the graph. For example, a `perturb_ratio` of 0.1 means that 10% of the current number of edges will be added as new random edges.
  * `rng`: An optionalrandom number generator to ensure reproducible results.

# Examples

```julia
julia> g = GNNGraph((s, t, w))
GNNGraph:
  num_nodes: 4
  num_edges: 5

julia> perturbed_g = perturb_edges(g, 0.2)
GNNGraph:
  num_nodes: 4
  num_edges: 6
```
