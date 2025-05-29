```
Rayleigh(σ)
```

The *Rayleigh distribution* with scale `σ` has probability density function

$$
f(x; \sigma) = \frac{x}{\sigma^2} e^{-\frac{x^2}{2 \sigma^2}}, \quad x > 0
$$

It is related to the [`Normal`](@ref) distribution via the property that if $X, Y \sim \operatorname{Normal}(0,\sigma)$, independently, then $\sqrt{X^2 + Y^2} \sim \operatorname{Rayleigh}(\sigma)$.

```julia
Rayleigh()       # Rayleigh distribution with unit scale, i.e. Rayleigh(1)
Rayleigh(σ)      # Rayleigh distribution with scale σ

params(d)        # Get the parameters, i.e. (σ,)
scale(d)         # Get the scale parameter, i.e. σ
```

External links

  * [Rayleigh distribution on Wikipedia](http://en.wikipedia.org/wiki/Rayleigh_distribution)
