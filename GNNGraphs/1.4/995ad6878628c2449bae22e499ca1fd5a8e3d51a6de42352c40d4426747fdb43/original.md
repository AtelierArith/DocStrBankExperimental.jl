```
normalized_laplacian(g, T=Float32; add_self_loops=false, dir=:out)
```

Normalized Laplacian matrix of graph `g`.

# Arguments

  * `g`: A `GNNGraph`.
  * `T`: result element type.
  * `add_self_loops`: add self-loops while calculating the matrix.
  * `dir`: the edge directionality considered (:out, :in, :both).
