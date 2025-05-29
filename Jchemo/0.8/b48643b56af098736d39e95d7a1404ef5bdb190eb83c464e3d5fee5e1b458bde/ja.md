```
normv(x)
normv(x, weights::Weight)
```

ベクトルのノルムを計算します。

  * `x` : ベクトル (n)。
  * `weights` : 観測の重み (n)。タイプ `Weight` でなければなりません（例えば、関数 `mweight` を参照）。

ベクトル `x` の重み付きノルムは次のように計算されます：

  * sqrt(x' * D * x)、ここで D はベクトル `weights.w` の対角行列です。

## 参考文献

@gdkrmr, https://discourse.julialang.org/t/julian-way-to-write-this-code/119348/17

@Stevengj,  https://discourse.julialang.org/t/interesting-post-about-simd-dot-product-and-cosine-similarity/123282.

## 例

```julia
using Jchemo

n = 1000
x = rand(n)
w = mweight(ones(n))

normv(x)
sqrt(n) * normv(x, w)
```
