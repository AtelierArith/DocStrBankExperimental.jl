```
gausslobatto(n::Integer) -> x, w  # nodes, weights
```

Return nodes `x` and weights `w` of [Gauss-Lobatto quadrature](https://mathworld.wolfram.com/LobattoQuadrature.html).

$$
\int_{-1}^{1} f(x) dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

# Examples

```jldoctest
julia> x, w = gausslobatto(4);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 2/5
true
```

Note that the both ends of nodes are fixed at -1 and 1.

```jldoctest
julia> x, w = gausslobatto(4);

julia> x[1], x[end]
(-1.0, 1.0)
```
