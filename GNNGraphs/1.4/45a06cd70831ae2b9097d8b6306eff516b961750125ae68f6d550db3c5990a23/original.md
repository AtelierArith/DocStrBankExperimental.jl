```
scaled_laplacian(g, T=Float32; dir=:out)
```

Scaled Laplacian matrix of graph `g`, defined as $\hat{L} = \frac{2}{\lambda_{max}} L - I$ where $L$ is the normalized Laplacian matrix.

# Arguments

  * `g`: A `GNNGraph`.
  * `T`: result element type.
  * `dir`: the edge directionality considered (:out, :in, :both).
