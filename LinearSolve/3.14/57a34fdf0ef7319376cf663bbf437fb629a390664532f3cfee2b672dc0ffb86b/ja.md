`QRFactorization(pivot=LinearAlgebra.NoPivot(),blocksize=16)`

Juliaの組み込み`qr`。`qr!(A)`を呼び出すのと同等です。

  * 密行列の場合、これはユーザーのコンピュータの現在のBLAS実装を使用します。デフォルトではOpenBLASですが、ユーザーがシステムで`using MKL`を実行するとMKLを使用します。
  * 疎行列の場合、これはSparseArraysからSPQRを使用します。
  * CuMatrixの場合、CuSolverからのCUDA加速QRを使用します。
  * BandedMatrixおよびBlockBandedMatrixの場合、バンドQRを使用します。
