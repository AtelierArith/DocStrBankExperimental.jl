```
moment(::Type{GaussianDistribution}, FirstMoment, μ, σ)
```

Analytic expression for the no-central `FirstMoment` from a [`GaussianDistribution`](@ref):

$$
M_1 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y = \mu. 
$$
