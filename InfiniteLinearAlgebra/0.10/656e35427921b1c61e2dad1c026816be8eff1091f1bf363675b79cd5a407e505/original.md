```
BidiagonalConjugation(U, X, V, uplo)
```

Efficiently compute the projection of the matrix product `inv(U)XV` onto a bidiagonal matrix. The `uplo` argument  specifies whether the projection is upper (`uplo = 'U'`) or lower (`uplo = 'L'`) bidiagonal. 

The computation is returned as a `Bidiagonal` matrix whose  diagonal and off-diagonal vectors are computed lazily.
