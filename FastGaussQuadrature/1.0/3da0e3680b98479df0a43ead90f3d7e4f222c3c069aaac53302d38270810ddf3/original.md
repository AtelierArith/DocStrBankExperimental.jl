```
gausshermite(n::Integer; normalize = false) -> x, w  # nodes, weights
```

Return nodes `x` and weights `w` of [Gauss-Hermite quadrature](https://en.wikipedia.org/wiki/Gauss%E2%80%93Hermite_quadrature).

$$
\int_{-\infty}^{+\infty} f(x) \exp(-x^2) dx \approx \sum_{i=1}^{n} w_i f(x_i)
$$

The option `normalize=true` instead computes

$$
\int_{-\infty}^{+\infty} f(x) \phi(x) dx \approx \sum_{i=1}^{n} w_i f(x_i),
$$

where $\phi$ is the standard normal density function.

# Examples

```jldoctest
julia> x, w = gausshermite(3);

julia> f(x) = x^4;

julia> I = dot(w, f.(x));

julia> I ≈ 3(√π)/4
true
```
