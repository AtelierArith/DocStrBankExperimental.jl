```
InverseGamma(α, θ)
```

The *inverse Gamma distribution* with shape parameter `α` and scale `θ` has probability density function

$$
f(x; \alpha, \theta) = \frac{\theta^\alpha x^{-(\alpha + 1)}}{\Gamma(\alpha)}
e^{-\frac{\theta}{x}}, \quad x > 0
$$

It is related to the [`Gamma`](@ref) distribution: if $X \sim \operatorname{Gamma}(\alpha, \beta)$, then $1 / X \sim \operatorname{InverseGamma}(\alpha, \beta^{-1})$.

```julia
InverseGamma()        # Inverse Gamma distribution with unit shape and unit scale, i.e. InverseGamma(1, 1)
InverseGamma(α)       # Inverse Gamma distribution with shape α and unit scale, i.e. InverseGamma(α, 1)
InverseGamma(α, θ)    # Inverse Gamma distribution with shape α and scale θ

params(d)        # Get the parameters, i.e. (α, θ)
shape(d)         # Get the shape parameter, i.e. α
scale(d)         # Get the scale parameter, i.e. θ
```

External links

  * [Inverse gamma distribution on Wikipedia](http://en.wikipedia.org/wiki/Inverse-gamma_distribution)
