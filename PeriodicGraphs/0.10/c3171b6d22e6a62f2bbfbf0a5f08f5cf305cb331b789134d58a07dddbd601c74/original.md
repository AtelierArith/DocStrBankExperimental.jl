```
PeriodicEdge{N} <: Graphs.SimpleGraphs.AbstractSimpleEdge{Int}
```

Edge type for an `N`-periodic graph.

An edge is uniquely determined by the vertex identifiers of its source and destination, and the cell offset between the source vertex and the destination vertex.
