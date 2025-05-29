```
gauss_seidel!(x, A::AbstractMatrix, b; maxiter=10) -> x
```

正確に `maxiter` 回のガウス・ザイデル反復を実行します。

完全にインプレースで動作し、`A` を列ごとに走査します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
