```
gausschebyshevv(n::Integer) -> x, w  # nodes, weights
```

Return nodes `x` and weights `w` of [Gauss-Chebyshev quadrature](https://en.wikipedia.org/wiki/Chebyshev%E2%80%93Gauss_quadrature) of the 3rd kind.

$$
\int_{-1}^{1} f(x)\sqrt{\frac{1+x}{1-x}} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# Examples

```jldoctest
julia> x, w = gausschebyshevv(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 3π/8
true
```
