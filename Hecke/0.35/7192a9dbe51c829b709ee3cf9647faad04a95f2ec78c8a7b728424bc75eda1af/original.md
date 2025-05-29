```
is_conjugate(M::ZZMatrix, N::ZZMatrix) -> Bool, ZZMatrix
```

Returns `true` and a matrix $U$ with $M = U\cdot N\cdot U^{-1}$ if such a matrix exists and `false` and $0$ otherwise. The characteristic polynomial of $M$ is required to be square-free.
