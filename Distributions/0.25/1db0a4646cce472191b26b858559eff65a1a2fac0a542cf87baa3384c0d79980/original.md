```
Cauchy(μ, σ)
```

The *Cauchy distribution* with location `μ` and scale `σ` has probability density function

$$
f(x; \mu, \sigma) = \frac{1}{\pi \sigma \left(1 + \left(\frac{x - \mu}{\sigma} \right)^2 \right)}
$$

```julia
Cauchy()         # Standard Cauchy distribution, i.e. Cauchy(0, 1)
Cauchy(μ)        # Cauchy distribution with location μ and unit scale, i.e. Cauchy(μ, 1)
Cauchy(μ, σ)     # Cauchy distribution with location μ and scale σ

params(d)        # Get the parameters, i.e. (μ, σ)
location(d)      # Get the location parameter, i.e. μ
scale(d)         # Get the scale parameter, i.e. σ
```

External links

  * [Cauchy distribution on Wikipedia](http://en.wikipedia.org/wiki/Cauchy_distribution)
