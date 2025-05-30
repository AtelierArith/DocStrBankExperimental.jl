`SVDFactorization(full=false,alg=LinearAlgebra.DivideAndConquer())`

Juliaの組み込み`svd`。`svd!(A)`と同等です。

  * 密行列に対して、これはユーザーのコンピュータの現在のBLAS実装を使用します。デフォルトではOpenBLASですが、ユーザーがシステムで`using MKL`を実行するとMKLを使用します。
