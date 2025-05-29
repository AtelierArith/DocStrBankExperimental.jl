```
has_isolated_nodes(g::GNNGraph; dir=:out)
```

Return true if the graph `g` contains nodes with out-degree (if `dir=:out`) or in-degree (if `dir = :in`) equal to zero.
