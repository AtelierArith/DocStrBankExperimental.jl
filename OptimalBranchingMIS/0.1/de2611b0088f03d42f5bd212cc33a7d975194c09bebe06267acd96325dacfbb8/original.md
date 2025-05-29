```
struct MinBoundarySelector <: AbstractSelector
```

The `MinBoundarySelector` struct represents a strategy for selecting a subgraph with the minimum number of open vertices by k-layers of neighbors.

# Fields

  * `k::Int`: The number of layers of neighbors to consider when selecting the subgraph.
