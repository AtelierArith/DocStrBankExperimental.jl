```
kernel_score = random_walk(adj_mat; l=n)
kernel_score = random_walk(g₁xg₂; l=n)
kernel_score = random_walk(g₁, g₂; l=n)
```

Returns the similarity score for two graphs by applying the `l`-length random walk graph kernel (random_walk) via their direct product graph.
