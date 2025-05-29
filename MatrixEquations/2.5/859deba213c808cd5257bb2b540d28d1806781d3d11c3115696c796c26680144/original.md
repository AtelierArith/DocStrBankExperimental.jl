```
 isschur(A::AbstractMatrix, B::AbstractMatrix) -> Bool
```

Test whether `(A,B)` is a pair of square matrices in a real or complex generalized Schur form. In the real case, it is only tested whether `B` is upper triangular and `A` is a quasi upper triangular matrix, which may have 2x2 diagonal blocks, which however must not correspond to complex conjugate eigenvalues. In the complex case, it is tested if `A` and `B` are both upper triangular.
