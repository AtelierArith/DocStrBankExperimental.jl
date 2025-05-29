```
InverseGaussian(μ,λ)
```

The *inverse Gaussian distribution* with mean `μ` and shape `λ` has probability density function

$$
f(x; \mu, \lambda) = \sqrt{\frac{\lambda}{2\pi x^3}}
\exp\!\left(\frac{-\lambda(x-\mu)^2}{2\mu^2x}\right), \quad x > 0
$$

```julia
InverseGaussian()              # Inverse Gaussian distribution with unit mean and unit shape, i.e. InverseGaussian(1, 1)
InverseGaussian(μ),            # Inverse Gaussian distribution with mean μ and unit shape, i.e. InverseGaussian(μ, 1)
InverseGaussian(μ, λ)          # Inverse Gaussian distribution with mean μ and shape λ

params(d)           # Get the parameters, i.e. (μ, λ)
mean(d)             # Get the mean parameter, i.e. μ
shape(d)            # Get the shape parameter, i.e. λ
```

External links

  * [Inverse Gaussian distribution on Wikipedia](http://en.wikipedia.org/wiki/Inverse_Gaussian_distribution)
