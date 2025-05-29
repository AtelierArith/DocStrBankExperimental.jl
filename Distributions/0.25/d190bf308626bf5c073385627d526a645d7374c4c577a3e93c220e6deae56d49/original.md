```
Exponential(θ)
```

The *Exponential distribution* with scale parameter `θ` has probability density function

$$
f(x; \theta) = \frac{1}{\theta} e^{-\frac{x}{\theta}}, \quad x > 0
$$

```julia
Exponential()      # Exponential distribution with unit scale, i.e. Exponential(1)
Exponential(θ)     # Exponential distribution with scale θ

params(d)          # Get the parameters, i.e. (θ,)
scale(d)           # Get the scale parameter, i.e. θ
rate(d)            # Get the rate parameter, i.e. 1 / θ
```

External links

  * [Exponential distribution on Wikipedia](http://en.wikipedia.org/wiki/Exponential_distribution)
