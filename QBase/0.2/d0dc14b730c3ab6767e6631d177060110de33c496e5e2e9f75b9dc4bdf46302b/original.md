```
commutes(A :: Matrix, B :: Matrix; atol=ATOL :: Float64) :: Bool
```

Returns true if matrix `A` commutes with matrix `B`. Two matrices commute if `A*B == B*A`. The matrices must have compatible dimensions:

  * A: Matrix, mxn dimensions
  * B: Matrix, nxm dimensions

A `DomainError` is thrown if the matrices are not compatible.
