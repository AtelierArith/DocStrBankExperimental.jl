```
add_nodes(g::GNNGraph, n; [ndata])
```

Add `n` new nodes to graph `g`. In the  new graph, these nodes will have indexes from `g.num_nodes + 1` to `g.num_nodes + n`.
