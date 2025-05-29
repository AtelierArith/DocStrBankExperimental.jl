```
gausschebyshevu(n::Integer) -> x, w  # nodes, weights
```

Return nodes `x` and weights `w` of [Gauss-Chebyshev quadrature](https://en.wikipedia.org/wiki/Chebyshev%E2%80%93Gauss_quadrature) of the 2nd kind.

$$
\int_{-1}^{1} f(x)\sqrt{1-x^2} dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# Examples

```jldoctest
julia> x, w = gausschebyshevu(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ π/16
true
```
