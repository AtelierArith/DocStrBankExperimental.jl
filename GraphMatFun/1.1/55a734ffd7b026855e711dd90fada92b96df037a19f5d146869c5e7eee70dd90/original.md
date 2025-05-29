```
compress_graph_redundant!(
    graph,
    cref = [];
    compress_lincomb = true,
    verbose = false,
)
```

Removes from the graph redundant nodes, that is, nodes that repeat a computation that is already present in the graph. Nodes corresponding to a linear combination are removed only if the coefficients are the same and `compress_lincomb` is set to `true`.
