```
degree(g::GNNHeteroGraph, edge_type::EType; dir = :in)
```

Return a vector containing the degrees of the nodes in `g` GNNHeteroGraph given `edge_type`.

# Arguments

  * `g`: A graph.
  * `edge_type`: A tuple of symbols `(source_t, edge_t, target_t)` representing the edge type.
  * `T`: Element type of the returned vector. If `nothing`, is      chosen based on the graph type. Default `nothing`.
  * `dir`: For `dir = :out` the degree of a node is counted based on the outgoing edges.        For `dir = :in`, the ingoing edges are used. If `dir = :both` we have the sum of the two.        Default `dir = :out`.
