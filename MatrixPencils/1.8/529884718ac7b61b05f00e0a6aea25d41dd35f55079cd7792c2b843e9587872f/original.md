```
isqtriu(A::AbstractMatrix) -> Bool
```

Test whether `A` is a square matrix in a quasi upper triangular form  (e.g., in real or complex Schur form). In the real case, `A` may have 2x2  diagonal blocks, which however must not correspond to complex conjugate eigenvalues.  In the complex case, it is tested if `A` is upper triangular.
