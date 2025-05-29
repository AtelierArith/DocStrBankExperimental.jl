```
Pareto(α,θ)
```

The *Pareto distribution* with shape `α` and scale `θ` has probability density function

$$
f(x; \alpha, \theta) = \frac{\alpha \theta^\alpha}{x^{\alpha + 1}}, \quad x \ge \theta
$$

```julia
Pareto()            # Pareto distribution with unit shape and unit scale, i.e. Pareto(1, 1)
Pareto(α)           # Pareto distribution with shape α and unit scale, i.e. Pareto(α, 1)
Pareto(α, θ)        # Pareto distribution with shape α and scale θ

params(d)        # Get the parameters, i.e. (α, θ)
shape(d)         # Get the shape parameter, i.e. α
scale(d)         # Get the scale parameter, i.e. θ
```

External links

  * [Pareto distribution on Wikipedia](http://en.wikipedia.org/wiki/Pareto_distribution)
