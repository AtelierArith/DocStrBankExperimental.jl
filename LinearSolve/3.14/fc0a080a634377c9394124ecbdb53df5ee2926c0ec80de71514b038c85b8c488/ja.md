`LUFactorization(pivot=LinearAlgebra.RowMaximum())`

Juliaの組み込み`lu`。`lu!(A)`を呼び出すのと同等です。

  * 密行列の場合、これはユーザーのコンピュータの現在のBLAS実装を使用します。デフォルトではOpenBLASですが、ユーザーがシステムで`using MKL`を実行するとMKLを使用します。
  * 疎行列の場合、これはSparseArraysからUMFPACKを使用します。これは、符号的因子分解をキャッシュしないことに注意してください。
  * CuMatrixの場合、CuSolverからのCUDA加速LUを使用します。
  * BandedMatrixおよびBlockBandedMatrixの場合、バンドLUを使用します。

## 位置引数

  * pivot: ピボッティングの選択。デフォルトは`LinearAlgebra.RowMaximum()`です。もう一つの選択肢は`LinearAlgebra.NoPivot()`です。
