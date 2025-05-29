```
gausslaguerre(n::Integer) -> x, w  # ノード、重み
```

[ガウス・ラグランジュ数値積分](https://en.wikipedia.org/wiki/Gauss%E2%80%93Laguerre_quadrature)のノード `x` と重み `w` を返します。

$$
\int_{0}^{+\infty} f(x) e^{-x} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# 例

```jldoctest
julia> x, w = gausslaguerre(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 24
true
```
