```
scaled_laplacian(g, [T=float(eltype(g))])
```

Scaled Laplacien matrix of graph `g`, defined as

$$
\hat{L} = \frac{2}{\lambda_{max}} \tilde{L} - I
$$

where $\tilde{L}$ is the normalized Laplacian matrix.

# Arguments

  * `g`: Should be a adjacency matrix, `FeaturedGraph`, `SimpleGraph`, `SimpleDiGraph` (from Graphs)   or `SimpleWeightedGraph`, `SimpleWeightedDiGraph` (from SimpleWeightedGraphs).
  * `T`: The element type of result degree vector. The default type is the element type of `g`.
