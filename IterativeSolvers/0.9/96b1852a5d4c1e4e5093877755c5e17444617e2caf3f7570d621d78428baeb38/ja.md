```
sor!(x, A::SparseMatrixCSC, b, ω::Real; maxiter=10)
```

正確に `maxiter` 回のSOR反復をリラクゼーションパラメータ `ω` で実行します。

一時的なベクトルを割り当て、対角インデックスを事前に計算します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
