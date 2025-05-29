```
subgraph(fg, nodes)
```

Returns a subgraph of type `FeaturedSubgraph` from a given featured graph `fg`. It constructs a subgraph by reserving `nodes` in a graph.

# Arguments

  * `fg::AbstractFeaturedGraph`: A base featured graph to construct a subgraph.
  * `nodes::AbstractVector`: It specifies nodes to be reserved from `fg`.
