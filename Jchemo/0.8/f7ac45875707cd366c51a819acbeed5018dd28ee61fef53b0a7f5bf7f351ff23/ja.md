```
sumv(x)
sumv(x, weights::Weight)
```

ベクトルの合計を計算します。

  * `x` : ベクトル (n)。
  * `weights` : 観測値の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

## 例

```julia
using Jchemo

n = 100
x = rand(n)
w = mweight(rand(n)) 

sumv(x)
sumv(x, w)
```
