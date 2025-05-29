```
GeneralizedPareto(μ, σ, ξ)
```

The *Generalized Pareto distribution* (GPD) with shape parameter `ξ`, scale `σ` and location `μ` has probability density function

$$
f(x; \mu, \sigma, \xi) = \begin{cases}
        \frac{1}{\sigma}(1 + \xi \frac{x - \mu}{\sigma} )^{-\frac{1}{\xi} - 1} & \text{for } \xi \neq 0 \\
        \frac{1}{\sigma} e^{-\frac{\left( x - \mu \right) }{\sigma}} & \text{for } \xi = 0
    \end{cases}~,
    \quad x \in \begin{cases}
        \left[ \mu, \infty \right] & \text{for } \xi \geq 0 \\
        \left[ \mu, \mu - \sigma / \xi \right] & \text{for } \xi < 0
    \end{cases}
$$

```julia
GeneralizedPareto()             # GPD with unit shape and unit scale, i.e. GeneralizedPareto(0, 1, 1)
GeneralizedPareto(ξ)            # GPD with shape ξ and unit scale, i.e. GeneralizedPareto(0, 1, ξ)
GeneralizedPareto(σ, ξ)         # GPD with shape ξ and scale σ, i.e. GeneralizedPareto(0, σ, ξ)
GeneralizedPareto(μ, σ, ξ)      # GPD with shape ξ, scale σ and location μ.

params(d)       # Get the parameters, i.e. (μ, σ, ξ)
location(d)     # Get the location parameter, i.e. μ
scale(d)        # Get the scale parameter, i.e. σ
shape(d)        # Get the shape parameter, i.e. ξ
```

External links

  * [Generalized Pareto distribution on Wikipedia](https://en.wikipedia.org/wiki/Generalized_Pareto_distribution)
