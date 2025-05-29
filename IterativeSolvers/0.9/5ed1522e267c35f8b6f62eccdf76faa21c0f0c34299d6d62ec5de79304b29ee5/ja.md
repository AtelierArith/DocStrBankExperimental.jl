```
ssor!(x, A::AbstractMatrix, b, ω::Real; maxiter=10) -> x
```

正確に `maxiter` 回のSSOR反復を緩和パラメータ `ω` で実行します。各反復は基本的にSORの前方*および*後方スイープです。

単一の一時ベクトルを割り当て、`A` を列ごとに走査します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
