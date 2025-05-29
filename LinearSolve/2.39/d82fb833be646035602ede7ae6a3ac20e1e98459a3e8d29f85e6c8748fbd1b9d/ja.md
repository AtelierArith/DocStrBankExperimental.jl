`NormalBunchKaufmanFactorization(rook = false)`

A fast factorization which uses a BunchKaufman factorization on A * A'. Can be much faster than LU factorization, but is not as numerically stable and thus should only be applied to well-conditioned matrices.

## Positional Arguments

  * rook: whether to perform rook pivoting. Defaults to false.
