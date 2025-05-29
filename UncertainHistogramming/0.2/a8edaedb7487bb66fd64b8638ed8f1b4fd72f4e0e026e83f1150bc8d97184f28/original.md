```
moment(::Type{UniformDistribution}, FirstMoment, val, err)
```

Analytic expression for the no-central `FirstMoment` from a [`UniformDistribution`](@ref):

$$
M_1 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y = x. 
$$
