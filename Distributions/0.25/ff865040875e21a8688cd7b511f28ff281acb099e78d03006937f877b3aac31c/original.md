```
SymTriangularDist(μ, σ)
```

The *Symmetric triangular distribution* with location `μ` and scale `σ` has probability density function

$$
f(x; \mu, \sigma) = \frac{1}{\sigma} \left( 1 - \left| \frac{x - \mu}{\sigma} \right| \right), \quad \mu - \sigma \le x \le \mu + \sigma
$$

```julia
SymTriangularDist()         # Symmetric triangular distribution with zero location and unit scale
SymTriangularDist(μ)        # Symmetric triangular distribution with location μ and unit scale
SymTriangularDist(μ, s)     # Symmetric triangular distribution with location μ and scale σ

params(d)       # Get the parameters, i.e. (μ, σ)
location(d)     # Get the location parameter, i.e. μ
scale(d)        # Get the scale parameter, i.e. σ
```
