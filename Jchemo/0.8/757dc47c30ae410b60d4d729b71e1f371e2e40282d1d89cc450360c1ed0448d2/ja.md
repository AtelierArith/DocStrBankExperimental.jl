```
mahsqchol(X, Y)
mahsqchol(X, Y, Uinv)
```

観測値（行）の `X` と `Y` の間の二乗マハラノビス距離（コレスキー分解を用いて）を計算します。

  * `X` : データ (n, p)。
  * `Y` : データ (m, p)。
  * `Uinv` : 共分散行列 S のコレスキー分解の上三角行列の逆行列。指定されていない場合、S は `X` の未修正共分散行列に対して分解されます。

`X` と `Y` がそれぞれ (n, p) および (m, p) の場合、次のようなオブジェクト (n, m) を返します：

  * i, j = 行 i の `X` と行 j の `Y` の間の距離。

## 例

```julia
using LinearAlgebra, StatsBase

X = rand(5, 3)
Y = rand(2, 3)

mahsqchol(X, Y)

S = cov(X, corrected = false)
U = cholesky(Hermitian(S)).U 
Uinv = inv(U)
mahsqchol(X, Y, Uinv)

mahsqchol(X[:, 1], 4)
mahsqchol(1, 4, sqrt(2.1))
```
