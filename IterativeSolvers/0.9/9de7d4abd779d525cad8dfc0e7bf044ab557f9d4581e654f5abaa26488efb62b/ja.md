```
gauss_seidel!(x, A::SparseMatrixCSC, b; maxiter=10) -> x
```

正確に `maxiter` 回のガウス・ザイデル反復を実行します。

完全にインプレースで動作しますが、対角インデックスを事前に計算します。

対角にゼロがある場合、`LinearAlgebra.SingularException` をスローします。このチェックは事前に一度行われます。
