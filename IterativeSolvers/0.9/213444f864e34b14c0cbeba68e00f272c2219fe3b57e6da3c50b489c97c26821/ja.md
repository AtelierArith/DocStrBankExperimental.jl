```
ssor!(x, A::SparseMatrixCSC, b, ω::Real; maxiter=10)
```

リラクゼーションパラメータ `ω` を用いて、正確に `maxiter` 回の SSOR イテレーションを実行します。各イテレーションは基本的に SOR の前方および後方スイープです。

一時的なベクトルを割り当て、対角インデックスを事前に計算します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
