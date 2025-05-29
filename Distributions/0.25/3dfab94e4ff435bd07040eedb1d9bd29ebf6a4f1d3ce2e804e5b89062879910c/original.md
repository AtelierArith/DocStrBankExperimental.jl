```
Beta(α, β)
```

The *Beta distribution* has probability density function

$$
f(x; \alpha, \beta) = \frac{1}{B(\alpha, \beta)}
 x^{\alpha - 1} (1 - x)^{\beta - 1}, \quad x \in [0, 1]
$$

The Beta distribution is related to the [`Gamma`](@ref) distribution via the property that if $X \sim \operatorname{Gamma}(\alpha)$ and $Y \sim \operatorname{Gamma}(\beta)$ independently, then $X / (X + Y) \sim \operatorname{Beta}(\alpha, \beta)$.

```julia
Beta()        # equivalent to Beta(1, 1)
Beta(α)       # equivalent to Beta(α, α)
Beta(α, β)    # Beta distribution with shape parameters α and β

params(d)     # Get the parameters, i.e. (α, β)
```

External links

  * [Beta distribution on Wikipedia](http://en.wikipedia.org/wiki/Beta_distribution)
