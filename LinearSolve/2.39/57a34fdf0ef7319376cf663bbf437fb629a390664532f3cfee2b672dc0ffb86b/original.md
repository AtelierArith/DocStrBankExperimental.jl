`QRFactorization(pivot=LinearAlgebra.NoPivot(),blocksize=16)`

Julia's built in `qr`. Equivalent to calling `qr!(A)`.

  * On dense matrices, this uses the current BLAS implementation of the user's computer which by default is OpenBLAS but will use MKL if the user does `using MKL` in their system.
  * On sparse matrices, this will use SPQR from SparseArrays
  * On CuMatrix, it will use a CUDA-accelerated QR from CuSolver.
  * On BandedMatrix and BlockBandedMatrix, it will use a banded QR.
