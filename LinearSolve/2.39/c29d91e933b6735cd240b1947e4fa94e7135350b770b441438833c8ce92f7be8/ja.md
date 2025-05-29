`NormalCholeskyFactorization(pivot = RowMaximum())`

A fast factorization which uses a Cholesky factorization on A * A'. Can be much faster than LU factorization, but is not as numerically stable and thus should only be applied to well-conditioned matrices.

## Positional Arguments

  * pivot: Defaults to RowMaximum(), but can be NoPivot()
