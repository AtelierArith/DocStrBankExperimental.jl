```
moment(::Type{GaussianDistribution}, FourthMoment, μ, σ)
```

Analytic expression for the no-central `FourthMoment` from a [`GaussianDistribution`](@ref):

$$
M_4 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y^4 = \mu^4 + 6\mu^2\sigma^2 + 3\sigma^4. 
$$
