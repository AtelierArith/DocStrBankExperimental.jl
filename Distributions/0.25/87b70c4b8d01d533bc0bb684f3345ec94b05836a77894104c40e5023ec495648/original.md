```
PGeneralizedGaussian(μ, α, p)
```

The *p-Generalized Gaussian distribution*, more commonly known as the exponential power or the generalized normal distribution, with scale `α`, location `μ`, and shape `p` has the probability density function

$$
f(x, \mu, \alpha, p) = \frac{p}{2\alpha\Gamma(1/p)} e^{-(\frac{|x-\mu|}{\alpha})^p} \quad x \in (-\infty, +\infty) , \alpha > 0, p > 0
$$

The p-Generalized Gaussian (GGD) is a parametric distribution that incorporates the normal (`p = 2`) and Laplacian (`p = 1`) distributions as special cases. As `p → ∞`, the distribution approaches the Uniform distribution on `[μ - α, μ + α]`.

```julia
PGeneralizedGaussian()           # GGD with location 0, scale √2, and shape 2 (the normal distribution)
PGeneralizedGaussian(μ, α, p)    # GGD with location μ, scale α, and shape p

params(d)                        # Get the parameters, i.e. (μ, α, p)
location(d)                      # Get the location parameter, μ
scale(d)                         # Get the scale parameter, α
shape(d)                         # Get the shape parameter, p
```

External Links

  * [Generalized Gaussian on Wikipedia](http://en.wikipedia.org/wiki/Generalized_normal_distribution)
  * [Reference implementation](https://www.researchgate.net/publication/254282790_Simulation_of_the_p-generalized_Gaussian_distribution)

```

```
