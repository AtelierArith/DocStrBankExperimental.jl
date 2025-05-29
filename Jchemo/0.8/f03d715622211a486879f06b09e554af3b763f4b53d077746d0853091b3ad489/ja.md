```
mahsq(X, Y)
mahsq(X, Y, Sinv)
```

`X` と `Y` の行間の二乗マハラノビス距離。

  * `X` : データ (n, p)。
  * `Y` : データ (m, p)。
  * `Sinv` : 共分散行列 S の逆行列。指定されていない場合、S は `X` の補正されていない共分散行列として計算されます。

`X` と `Y` がそれぞれ (n, p) と (m, p) の場合、次のようなオブジェクト (n, m) を返します：

  * i, j = `X` の行 i と `Y` の行 j の間の距離。

## 例

```julia
using StatsBase 

X = rand(5, 3)
Y = rand(2, 3)

mahsq(X, Y)

S = cov(X, corrected = false)
Sinv = inv(S)
mahsq(X, Y, Sinv)
mahsq(X[1:1, :], Y[1:1, :], Sinv)

mahsq(X[:, 1], 4)
mahsq(1, 4, 2.1)
```
