```
Weibull(α,θ)
```

The *Weibull distribution* with shape `α` and scale `θ` has probability density function

$$
f(x; \alpha, \theta) = \frac{\alpha}{\theta} \left( \frac{x}{\theta} \right)^{\alpha-1} e^{-(x/\theta)^\alpha},
    \quad x \ge 0
$$

```julia
Weibull()        # Weibull distribution with unit shape and unit scale, i.e. Weibull(1, 1)
Weibull(α)       # Weibull distribution with shape α and unit scale, i.e. Weibull(α, 1)
Weibull(α, θ)    # Weibull distribution with shape α and scale θ

params(d)        # Get the parameters, i.e. (α, θ)
shape(d)         # Get the shape parameter, i.e. α
scale(d)         # Get the scale parameter, i.e. θ
```

External links

  * [Weibull distribution on Wikipedia](http://en.wikipedia.org/wiki/Weibull_distribution)
