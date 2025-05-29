```
gausslaguerre(n::Integer) -> x, w  # nodes, weights
```

Return nodes `x` and weights `w` of [Gauss-Laguerre quadrature](https://en.wikipedia.org/wiki/Gauss%E2%80%93Laguerre_quadrature).

$$
\int_{0}^{+\infty} f(x) e^{-x} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# Examples

```jldoctest
julia> x, w = gausslaguerre(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 24
true
```
