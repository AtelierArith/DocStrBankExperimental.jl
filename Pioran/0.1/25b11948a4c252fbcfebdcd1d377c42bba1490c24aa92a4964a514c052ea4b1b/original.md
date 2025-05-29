A scalable Gaussian process has a covariance function formed of semi-separable kernels

# Example

```julia
using Pioran
𝓟 = SingleBendingPowerLaw(1.0, 1.0, 2.0)
𝓡 = approx(𝓟, 1e-4, 1e-1, 30, 2.31,basis_function="SHO")
μ = 1.2

f = ScalableGP(𝓡) # zero-mean GP
f = ScalableGP(μ, 𝓡) # with mean μ
```

See [Foreman-Mackey et al. (2017)](https://ui.adsabs.harvard.edu/abs/2017AJ....154..220F) for more details.
