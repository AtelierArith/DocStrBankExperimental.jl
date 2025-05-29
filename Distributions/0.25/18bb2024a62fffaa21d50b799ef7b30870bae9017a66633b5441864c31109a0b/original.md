```
Rician(ν, σ)
```

The *Rician distribution* with parameters `ν` and `σ` has probability density function:

$$
f(x; \nu, \sigma) = \frac{x}{\sigma^2} \exp\left( \frac{-(x^2 + \nu^2)}{2\sigma^2} \right) I_0\left( \frac{x\nu}{\sigma^2} \right).
$$

If shape and scale parameters `K` and `Ω` are given instead, `ν` and `σ` may be computed from them:

$$
\sigma = \sqrt{\frac{\Omega}{2(K + 1)}}, \quad \nu = \sigma\sqrt{2K}
$$

```julia
Rician()         # Rician distribution with parameters ν=0 and σ=1
Rician(ν, σ)     # Rician distribution with parameters ν and σ

params(d)        # Get the parameters, i.e. (ν, σ)
shape(d)         # Get the shape parameter K = ν²/2σ²
scale(d)         # Get the scale parameter Ω = ν² + 2σ²
```

External links:

  * [Rician distribution on Wikipedia](https://en.wikipedia.org/wiki/Rice_distribution)
