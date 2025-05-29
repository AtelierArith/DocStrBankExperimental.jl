```
laplacian_lambda_max(g::GNNGraph, T=Float32; add_self_loops=false, dir=:out)
```

Return the largest eigenvalue of the normalized symmetric Laplacian of the graph `g`.

If the graph is batched from multiple graphs, return the list of the largest eigenvalue for each graph.
