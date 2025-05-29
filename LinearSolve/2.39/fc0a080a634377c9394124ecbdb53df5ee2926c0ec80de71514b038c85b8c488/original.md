`LUFactorization(pivot=LinearAlgebra.RowMaximum())`

Julia's built in `lu`. Equivalent to calling `lu!(A)`

  * On dense matrices, this uses the current BLAS implementation of the user's computer, which by default is OpenBLAS but will use MKL if the user does `using MKL` in their system.
  * On sparse matrices, this will use UMFPACK from SparseArrays. Note that this will not cache the symbolic factorization.
  * On CuMatrix, it will use a CUDA-accelerated LU from CuSolver.
  * On BandedMatrix and BlockBandedMatrix, it will use a banded LU.

## Positional Arguments

  * pivot: The choice of pivoting. Defaults to `LinearAlgebra.RowMaximum()`. The other choice is `LinearAlgebra.NoPivot()`.
