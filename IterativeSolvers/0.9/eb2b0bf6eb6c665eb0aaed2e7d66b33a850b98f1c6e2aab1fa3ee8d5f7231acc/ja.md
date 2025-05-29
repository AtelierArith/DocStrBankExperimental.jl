```
jacobi!(x, A::AbstractMatrix, b; maxiter=10) -> x
```

ちょうど `maxiter` 回のヤコビ反復を実行します。

単一の一時ベクトルを割り当て、`A` を列ごとに走査します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
