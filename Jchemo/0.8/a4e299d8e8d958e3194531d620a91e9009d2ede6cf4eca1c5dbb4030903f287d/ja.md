```
colvar(X)
colvar(X, weights::Weight)
```

行列の列ごとの分散（未修正）を計算します。

  * `X` : データ (n, p)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

ベクトルを返します。

## 例

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
w = mweight(rand(n))

colvar(X)
colvar(X, w)
```
