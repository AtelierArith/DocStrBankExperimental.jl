```
Stable(α, β, σ, μ)
```

The *Stable distribution* with stability index 0 < `α` ≤ 2, skewness parameter -1 ≤ `β` ≤ 1, scale 0 < `σ` and location `μ` has characteristic function

$$
\varphi(t; \alpha, \beta, \sigma, \mu) = \exp\big(\mathrm i t\mu -|\sigma t|^\alpha(1-\mathrm i\beta\mathrm{sgn}(t)\Phi(t))\big)
$$

with $\Phi(t) = -\frac{2}{\pi}\log|t|$ for α = 1 or $\Phi(t) = \tan(\pi\alpha/2)$ for α ≠ 1. We use type-1 parametrization.

```julia
Stable(α)             # standard symmetric α-Stable distribution equivalent to Stable(α, 0, 1, 0)
Stable(α, β)          # standard α-Stable distribution with skewness parameter β equivalent to S(α, β, 1, 0)
Stable(α, β, σ, μ)    # α-Stable distribution with skewness parameter β, scale σ and location μ

params(d)             # Get the parameters, i.e. (α, β, σ, μ)
shape(d)              # Get the shape, i.e. (α, β)
location(d)           # Get the location, i.e. μ
scale(d)              # Get the scale, i.e. σ
minimum(d)            # Get the lower bound
maximum(d)            # Get the upper bound
```

External links

  * [Stable distribution on Wikipedia](https://en.wikipedia.org/wiki/Stable_distribution)
