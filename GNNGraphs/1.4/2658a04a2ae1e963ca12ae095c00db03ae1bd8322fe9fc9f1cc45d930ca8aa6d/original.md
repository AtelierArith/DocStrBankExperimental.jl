```
getgraph(g::GNNGraph, i; nmap=false)
```

Return the subgraph of `g` induced by those nodes `j` for which `g.graph_indicator[j] == i` or, if `i` is a collection, `g.graph_indicator[j] ∈ i`.  In other words, it extract the component graphs from a batched graph. 

If `nmap=true`, return also a vector `v` mapping the new nodes to the old ones.  The node `i` in the subgraph will correspond to the node `v[i]` in `g`.
