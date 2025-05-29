```
Levy(μ, σ)
```

The *Lévy distribution* with location `μ` and scale `σ` has probability density function

$$
f(x; \mu, \sigma) = \sqrt{\frac{\sigma}{2 \pi (x - \mu)^3}}
\exp \left( - \frac{\sigma}{2 (x - \mu)} \right), \quad x > \mu
$$

```julia
Levy()         # Levy distribution with zero location and unit scale, i.e. Levy(0, 1)
Levy(μ)        # Levy distribution with location μ and unit scale, i.e. Levy(μ, 1)
Levy(μ, σ)     # Levy distribution with location μ and scale σ

params(d)      # Get the parameters, i.e. (μ, σ)
location(d)    # Get the location parameter, i.e. μ
```

External links

  * [Lévy distribution on Wikipedia](http://en.wikipedia.org/wiki/Lévy_distribution)
