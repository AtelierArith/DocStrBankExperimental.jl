```
Frechet(α,θ)
```

The *Fréchet distribution* with shape `α` and scale `θ` has probability density function

$$
f(x; \alpha, \theta) = \frac{\alpha}{\theta} \left( \frac{x}{\theta} \right)^{-\alpha-1}
e^{-(x/\theta)^{-\alpha}}, \quad x > 0
$$

```julia
Frechet()        # Fréchet distribution with unit shape and unit scale, i.e. Frechet(1, 1)
Frechet(α)       # Fréchet distribution with shape α and unit scale, i.e. Frechet(α, 1)
Frechet(α, θ)    # Fréchet distribution with shape α and scale θ

params(d)        # Get the parameters, i.e. (α, θ)
shape(d)         # Get the shape parameter, i.e. α
scale(d)         # Get the scale parameter, i.e. θ
```

External links

  * [Fréchet_distribution on Wikipedia](http://en.wikipedia.org/wiki/Fréchet_distribution)
