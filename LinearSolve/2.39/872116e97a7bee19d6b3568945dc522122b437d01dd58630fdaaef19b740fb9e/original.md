`SVDFactorization(full=false,alg=LinearAlgebra.DivideAndConquer())`

Julia's built in `svd`. Equivalent to `svd!(A)`.

  * On dense matrices, this uses the current BLAS implementation of the user's computer which by default is OpenBLAS but will use MKL if the user does `using MKL` in their system.
