```
moment(::Type{UniformDistribution}, ThirdMoment, val, err)
```

Analytic expression for the no-central `ThirdMoment` from a [`UniformDistribution`](@ref):

$$
M_3 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y^3 = x\left(x^2 + \epsilon^2 \right). 
$$
