```
Logistic(μ,θ)
```

The *Logistic distribution* with location `μ` and scale `θ` has probability density function

$$
f(x; \mu, \theta) = \frac{1}{4 \theta} \mathrm{sech}^2
\left( \frac{x - \mu}{2 \theta} \right)
$$

```julia
Logistic()       # Logistic distribution with zero location and unit scale, i.e. Logistic(0, 1)
Logistic(μ)      # Logistic distribution with location μ and unit scale, i.e. Logistic(μ, 1)
Logistic(μ, θ)   # Logistic distribution with location μ and scale θ

params(d)       # Get the parameters, i.e. (μ, θ)
location(d)     # Get the location parameter, i.e. μ
scale(d)        # Get the scale parameter, i.e. θ
```

External links

  * [Logistic distribution on Wikipedia](http://en.wikipedia.org/wiki/Logistic_distribution)
