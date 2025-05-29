```
euclsq(X, Y)
```

`X` と `Y` の行間の二乗ユークリッド距離。

  * `X` : データ (n, p)。
  * `Y` : データ (m, p)。

`X`(n, p) と `Y` (m, p) に対して、この関数は (n, m) のオブジェクトを返します：

  * i, j = `X` の行 i と `Y` の行 j の間の距離。

## 例

```julia
X = rand(5, 3)
Y = rand(2, 3)

euclsq(X, Y)

euclsq(X[1:1, :], Y[1:1, :])

euclsq(X[:, 1], 4)
euclsq(1, 4)
```
