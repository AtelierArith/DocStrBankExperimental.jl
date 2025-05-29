`CholeskyFactorization(; pivot = nothing, tol = 0.0, shift = 0.0, perm = nothing)`

Julia's built in `cholesky`. Equivalent to calling `cholesky!(A)`.

## Keyword Arguments

  * pivot: defaluts to NoPivot, can also be RowMaximum.
  * tol: the tol argument in CHOLMOD. Only used for sparse matrices.
  * shift: the shift argument in CHOLMOD. Only used for sparse matrices.
  * perm: the perm argument in CHOLMOD. Only used for sparse matrices.
