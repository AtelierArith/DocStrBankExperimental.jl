```
rqupdate!(R, Y) -> R
```

Update the upper triangular factor `R` by the upper triangular factor of the RQ factorization  of `[ Y R]`, where `Y` is a low-rank matrix `Y` (typically with one or two columns). The computation of `R` only uses `O(n^2)` operations (`n` is the size of `R`). The input matrix `R` is updated in place and the matrix `Y` is destroyed during the computation.
