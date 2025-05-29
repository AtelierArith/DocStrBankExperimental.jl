```
moment(::Type{UniformDistribution}, SecondMoment, val, err)
```

Analytic expression for the no-central `SecondMoment` from a [`UniformDistribution`](@ref):

$$
M_2 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y^2 = x^2 + \frac{1}{3}\epsilon^2. 
$$
