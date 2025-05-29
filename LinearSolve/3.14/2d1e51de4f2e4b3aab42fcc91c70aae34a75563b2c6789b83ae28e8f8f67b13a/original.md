`GenericLUFactorization(pivot=LinearAlgebra.RowMaximum())`

Julia's built in generic LU factorization. Equivalent to calling LinearAlgebra.generic_lufact!. Supports arbitrary number types but does not achieve as good scaling as BLAS-based LU implementations. Has low overhead and is good for small matrices.

## Positional Arguments

  * pivot: The choice of pivoting. Defaults to `LinearAlgebra.RowMaximum()`. The other choice is `LinearAlgebra.NoPivot()`.
