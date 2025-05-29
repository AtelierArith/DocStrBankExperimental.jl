```
reduce_nodes(aggr, indicator::AbstractVector, x)
```

Return the graph-wise aggregation of the node features `x` given the graph indicator `indicator`. The aggregation operator `aggr` can be `+`, `mean`, `max`, or `min`.

See also [`graph_indicator`](@ref).
