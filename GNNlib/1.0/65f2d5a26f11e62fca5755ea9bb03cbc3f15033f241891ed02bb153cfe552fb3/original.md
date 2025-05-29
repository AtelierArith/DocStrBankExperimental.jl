```
reduce_nodes(aggr, g, x)
```

For a batched graph `g`, return the graph-wise aggregation of the node features `x`. The aggregation operator `aggr` can be `+`, `mean`, `max`, or `min`. The returned array will have last dimension `g.num_graphs`.

See also: [`reduce_edges`](@ref).
