```
jacobi!(x, A::SparseMatrixCSC, b; maxiter=10) -> x
```

正確に `maxiter` 回のヤコビ反復を実行します。

一時的なベクトルを割り当て、対角インデックスを事前に計算します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
