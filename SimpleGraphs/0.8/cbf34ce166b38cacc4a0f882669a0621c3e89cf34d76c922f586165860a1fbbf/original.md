`bisect(G::UndirectedGraph)` partitions the vertex set of `G` using the eigenvector associated with the second smallest eigenvalue of the graph's Laplacian matrix (called `x` below).

This can be invoked as follows:

  * `bisect(G,"user",pivot)` splits the vertices `v` depending on `x[v] >= pivot` vs. `x[v] < pivot`.
  * `bisect(G,"zero")` is the same as `bisect(G,"user", 0.0)`.
  * `bisect(G,"median")` is equivalent to `bisect(G,"user",m)` where `m` is the median value of `x`.
  * `bisect(G,"equal")` creates a partition in which the two parts have sizes the differ by at most 1.

A plain call to `bisect(G)` is equivalent to `bisect(G,"zero")` (which is the same as `bisect(G,"user", 0.0)`).
