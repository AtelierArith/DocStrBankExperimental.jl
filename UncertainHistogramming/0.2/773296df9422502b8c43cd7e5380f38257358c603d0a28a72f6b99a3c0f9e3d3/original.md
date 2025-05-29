```
moment(::Type{GaussianDistribution}, ThirdMoment, μ, σ)
```

Analytic expression for the no-central `ThirdMoment` from a [`GaussianDistribution`](@ref):

$$
M_3 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y^3 = \mu^3 + 3\mu\sigma^2. 
$$
