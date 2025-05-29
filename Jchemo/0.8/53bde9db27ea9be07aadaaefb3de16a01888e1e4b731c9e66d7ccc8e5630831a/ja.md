```
varv(x)
varv(x, weights::Weight)
```

ベクトルの未修正分散を計算します。

  * `x` : ベクトル (n)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

## 例

```julia
using Jchemo

n = 1000
x = rand(n)
w = mweight(rand(n))

varv(x)
varv(x, w)
```
