```
S, P, B = balance(A[, perm=true])
```

Compute a similarity transform `T = S*P` resulting in `B = T\A*T` such that the row and column norms of `B` are approximately equivalent. If `perm=false`, the transformation will only scale `A` using diagonal `S`, and not permute `A` (i.e., set `P=I`).
