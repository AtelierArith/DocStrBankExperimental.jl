```
Gumbel(μ, θ)
```

The *Gumbel (maxima) distribution*  with location `μ` and scale `θ` has probability density function

$$
f(x; \mu, \theta) = \frac{1}{\theta} e^{-(z + e^{-z})},
\quad \text{ with } z = \frac{x - \mu}{\theta}
$$

```julia
Gumbel()            # Gumbel distribution with zero location and unit scale, i.e. Gumbel(0, 1)
Gumbel(μ)           # Gumbel distribution with location μ and unit scale, i.e. Gumbel(μ, 1)
Gumbel(μ, θ)        # Gumbel distribution with location μ and scale θ

params(d)        # Get the parameters, i.e. (μ, θ)
location(d)      # Get the location parameter, i.e. μ
scale(d)         # Get the scale parameter, i.e. θ
```

External links

  * [Gumbel distribution on Wikipedia](http://en.wikipedia.org/wiki/Gumbel_distribution)
