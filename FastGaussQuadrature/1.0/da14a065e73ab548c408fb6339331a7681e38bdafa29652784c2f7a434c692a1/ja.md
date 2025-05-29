```
gausschebyshevw(n::Integer) -> x, w  # ノード、重み
```

4種類の[ガウス・チェビシェフ数値積分](https://en.wikipedia.org/wiki/Chebyshev%E2%80%93Gauss_quadrature)のノード `x` と重み `w` を返します。

$$
\int_{-1}^{1} f(x)\sqrt{\frac{1-x}{1+x}} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# 例

```jldoctest
julia> x, w = gausschebyshevw(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 3π/8
true
```
