```
cosv(x, y)
```

2つのベクトル間の未修正共分散を計算します。

  * `x` : ベクトル (n).
  * `y` : ベクトル (n).

## 参考文献

@Stevengj,  https://discourse.julialang.org/t/interesting-post-about-simd-dot-product-and-cosine-similarity/123282.

## 例

```julia
using Jchemo

n = 5
x = rand(n)
y = rand(n)

covv(x, y)
```
