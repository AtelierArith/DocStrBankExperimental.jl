```
struct MinBoundaryHighDegreeSelector <: AbstractVertexSelector
```

The `MinBoundaryHighDegreeSelector` struct represents a strategy:     - if exists a vertex with degree geq high*degree*threshold, then select it and its k-degree neighbors.     - otherwise, select a subgraph with the minimum number of open vertices by k-layers of neighbors.

# Fields

  * `kb::Int`: The number of layers of neighbors to consider when selecting the subgraph.
  * `hd::Int`: The threshold of degree for a vertex to be selected.
  * `kd::Int`: The number of layers of neighbors to consider when selecting the subgraph.
