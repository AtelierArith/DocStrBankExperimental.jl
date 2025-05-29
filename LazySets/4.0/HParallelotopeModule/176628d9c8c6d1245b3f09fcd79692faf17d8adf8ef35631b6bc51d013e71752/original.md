```
extremal_vertices(P::HParallelotope{N, VN}) where {N, VN}
```

Compute the extremal vertices with respect to the base vertex of a parallelotope in constraint representation.

### Input

  * `P` – parallelotope in constraint representation

### Output

The list of vertices connected to the base vertex of $P$.

### Notes

Let $P$ be a parallelotope in constraint representation with directions matrix $D$ and offset vector $c$. The *extremal vertices* of $P$ with respect to its base vertex $q$ are those vertices of $P$ that have an edge in common with $q$.

### Algorithm

The extremal vertices can be computed as the solution of the $n$-dimensional linear systems of equations $D x = v_i$ where for each $i = 1, …, n$, $v_i = [-c_{n+1}, …, c_i, …, -c_{2n}]$.

We refer to [DreossiDP17; Section 3.2.1](@citet) for details.
