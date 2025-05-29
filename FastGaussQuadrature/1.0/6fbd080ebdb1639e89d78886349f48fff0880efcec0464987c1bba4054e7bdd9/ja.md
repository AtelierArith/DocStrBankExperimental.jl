```
gausschebyshevu(n::Integer) -> x, w  # ノード、重み
```

2次の[ガウス・チェビシェフ積分法](https://en.wikipedia.org/wiki/Chebyshev%E2%80%93Gauss_quadrature)のノード `x` と重み `w` を返します。

$$
\int_{-1}^{1} f(x)\sqrt{1-x^2} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# 例

```jldoctest
julia> x, w = gausschebyshevu(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ π/16
true
```
