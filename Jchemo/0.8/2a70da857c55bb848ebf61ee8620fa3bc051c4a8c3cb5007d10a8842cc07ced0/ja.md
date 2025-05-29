```
stdv(x)
stdv(x, weights::Weight)
```

ベクトルの不正規化標準偏差を計算します。

  * `x` : ベクトル (n)。
  * `weights` : 観測値の重み (n)。    `Weight` 型でなければなりません（例えば、関数 `mweight` を参照）。

## 例

```julia
using Jchemo

n = 1000
x = rand(n)
w = mweight(rand(n))

stdv(x)
stdv(x, w)
```
