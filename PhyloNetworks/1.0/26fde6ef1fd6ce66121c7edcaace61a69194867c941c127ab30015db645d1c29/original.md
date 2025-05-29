```
preorder!(net::HybridNetwork)
```

Update attribute `net.vec_node` in which the nodes are pre-ordered (also called topological sorting), such that each node is visited after its parent(s). The edges' direction needs to be correct before calling `preorder!`, using `directedges!`
