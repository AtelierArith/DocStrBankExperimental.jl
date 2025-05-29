```
is_unitary( U :: Matrix; atol=ATOL :: Float64 ) :: Bool
```

Returns `true` if matrix `U` is unitary. The hermitian adjoint of a unitary matrix is its inverse:

  * `U' * U == I` where `I` is the identity matrix.
