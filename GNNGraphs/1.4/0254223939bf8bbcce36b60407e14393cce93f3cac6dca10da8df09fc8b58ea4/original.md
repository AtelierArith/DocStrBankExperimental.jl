```
add_self_loops(g::GNNGraph)
```

Return a graph with the same features as `g` but also adding edges connecting the nodes to themselves.

Nodes with already existing self-loops will obtain a second self-loop.

If the graphs has edge weights, the new edges will have weight 1.
