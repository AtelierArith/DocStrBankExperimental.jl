```
TruncBond{T} <: SVDTrunc
```

ボンドサイズ `m'` に基づいてSVDベースの切り捨てを行うために使用される型です。ベクトル $\lambda$ に $m$ 個の特異値が与えられた場合、$m'$ 個の最大の特異値のみが保持され、他はゼロに切り捨てられます。

# フィールド

  * `mprime`: 保持する特異値の数

```@example
svd_trunc = TruncBond(3)
M = rand(5,6)
M_trunc = svd_trunc(M)
```
