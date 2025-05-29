```
degree(g::GNNGraph, T=nothing; dir=:out, edge_weight=true)
```

Return a vector containing the degrees of the nodes in `g`.

The gradient is propagated through this function only if `edge_weight` is `true` or a vector.

# Arguments

  * `g`: A graph.
  * `T`: Element type of the returned vector. If `nothing`, is      chosen based on the graph type and will be an integer      if `edge_weight = false`. Default `nothing`.
  * `dir`: For `dir = :out` the degree of a node is counted based on the outgoing edges.        For `dir = :in`, the ingoing edges are used. If `dir = :both` we have the sum of the two.
  * `edge_weight`: If `true` and the graph contains weighted edges, the degree will                be weighted. Set to `false` instead to just count the number of               outgoing/ingoing edges.                Finally, you can also pass a vector of weights to be used               instead of the graph's own weights.               Default `true`.
