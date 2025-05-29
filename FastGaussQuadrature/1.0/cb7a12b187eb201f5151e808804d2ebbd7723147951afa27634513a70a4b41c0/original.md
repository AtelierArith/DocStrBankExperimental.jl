```
gaussradau(n::Integer) -> x, w  # nodes, weights
```

Return nodes `x` and weights `w` of [Gauss-Radau quadrature](https://mathworld.wolfram.com/RadauQuadrature.html).

$$
\int_{-1}^{1} f(x) dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# Examples

```jldoctest
julia> x, w = gaussradau(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 2/5
true
```

Note that the first node is fixed at -1.

```jldoctest
julia> x, w = gaussradau(3);

julia> x[1]
-1.0
```
