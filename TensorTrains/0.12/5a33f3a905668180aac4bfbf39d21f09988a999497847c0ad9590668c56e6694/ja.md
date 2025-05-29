```
TruncThresh{T} <: SVDTrunc
```

閾値 `ε` に基づいて SVD ベースの切り捨てを実行するために使用される型です。$m$ 個の特異値のベクトル $\lambda$ が与えられたとき、$\varepsilon\sqrt{\sum_{k=1}^m \lambda_k^2}$ 未満のものはゼロに切り捨てられます。

# フィールド

  * `ε`: 閾値。

```@example
svd_trunc = TruncThresh(1e-5)
M = rand(5,6)
M_trunc = svd_trunc(M)
```
