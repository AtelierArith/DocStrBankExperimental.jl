```
is_sublattice_with_relations(M::ZZLat, N::ZZLat) -> Bool, QQMatrix
```

Returns whether $N$ is a sublattice of $M$. In this case, the second return value is a matrix $B$ such that $B B_M = B_N$, where $B_M$ and $B_N$ are the basis matrices of $M$ and $N$ respectively.
