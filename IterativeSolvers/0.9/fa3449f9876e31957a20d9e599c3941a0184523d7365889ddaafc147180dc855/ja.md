```
sor!(x, A::AbstractMatrix, b, ω::Real; maxiter=10) -> x
```

リラクゼーションパラメータ `ω` を用いて、正確に `maxiter` 回のSOR反復を実行します。

単一の一時ベクトルを割り当て、`A` を列ごとに走査します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
