```
GeneralizedExtremeValue(μ, σ, ξ)
```

The *Generalized extreme value distribution* with shape parameter `ξ`, scale `σ` and location `μ` has probability density function

$$
f(x; \xi, \sigma, \mu) = \begin{cases}
        \frac{1}{\sigma} \left[ 1+\left(\frac{x-\mu}{\sigma}\right)\xi\right]^{-1/\xi-1} \exp\left\{-\left[ 1+ \left(\frac{x-\mu}{\sigma}\right)\xi\right]^{-1/\xi} \right\} & \text{for } \xi \neq 0  \\
        \frac{1}{\sigma} \exp\left\{-\frac{x-\mu}{\sigma}\right\} \exp\left\{-\exp\left[-\frac{x-\mu}{\sigma}\right]\right\} & \text{for } \xi = 0 \\
    \end{cases}
$$

for

$$
x \in \begin{cases}
        \left[ \mu - \frac{\sigma}{\xi}, + \infty \right) & \text{for } \xi > 0 \\
        \left( - \infty, + \infty \right) & \text{for } \xi = 0 \\
        \left( - \infty, \mu - \frac{\sigma}{\xi} \right] & \text{for } \xi < 0
    \end{cases}
$$

```julia
GeneralizedExtremeValue(μ, σ, ξ)      # Generalized Pareto distribution with shape ξ, scale σ and location μ.

params(d)       # Get the parameters, i.e. (μ, σ, ξ)
location(d)     # Get the location parameter, i.e. μ
scale(d)        # Get the scale parameter, i.e. σ
shape(d)        # Get the shape parameter, i.e. ξ (sometimes called c)
```

External links

  * [Generalized extreme value distribution on Wikipedia](https://en.wikipedia.org/wiki/Generalized_extreme_value_distribution)
