```
compress_graph_dangling!(graph,cref=[];verbose=false)
```

Removes dangling nodes in the graph. If a node is not used anywhere and it is not in the output, it can safely be removed.
