```
moment(::Type{GaussianDistribution}, SecondMoment, μ, σ)
```

Analytic expression for the no-central `SecondMoment` from a [`GaussianDistribution`](@ref):

$$
M_2 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y^2 = \mu^2 + \sigma^2. 
$$
