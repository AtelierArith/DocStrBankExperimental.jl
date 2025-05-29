```
colstd(X)
colstd(X, weights::Weight)
```

行列の列ごとの標準偏差（修正なし）を計算します。

  * `X` : データ (n, p)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

ベクトルを返します。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
w = mweight(rand(n))

colstd(X)
colstd(X, w)
```
