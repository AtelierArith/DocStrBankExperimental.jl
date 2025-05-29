```
 isschur(A::AbstractMatrix) -> Bool
```

Test whether `A` is a square matrix in a real or complex Schur form. In the real case, it is only tested whether A is a quasi upper triangular matrix, which may have 2x2 diagonal blocks, which however must not correspond to complex conjugate eigenvalues. In the complex case, it is tested if `A` is upper triangular.
