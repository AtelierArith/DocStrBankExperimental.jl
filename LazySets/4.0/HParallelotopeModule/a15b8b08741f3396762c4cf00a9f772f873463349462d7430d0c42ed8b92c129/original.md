```
base_vertex(P::HParallelotope)
```

Compute the base vertex of a parallelotope in constraint representation.

### Input

  * `P` – parallelotope in constraint representation

### Output

The base vertex of `P`.

### Algorithm

Intuitively, the base vertex is the point from which we get the relative positions of all the other points. The base vertex can be computed as the solution of the $n$-dimensional linear system $D_i x = c_{n+i}$ for $i = 1, …, n$, see [DreossiDP17; Section 3.2.1](@citet).
