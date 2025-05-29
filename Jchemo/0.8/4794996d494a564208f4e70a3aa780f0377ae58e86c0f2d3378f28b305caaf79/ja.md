```
meanv(x)
meanv(x, weights::Weight)
```

ベクトルの平均を計算します。

  * `x` : ベクトル (n)。
  * `weights` : 観測値の重み (n)。 `Weight` 型でなければなりません（例えば、関数 `mweight` を参照してください）。

## 例

```julia
using Jchemo

n = 100
x = rand(n)
w = mweight(rand(n)) 

meanv(x)
meanv(x, w)
```
