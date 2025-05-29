```
moment(::Type{UniformDistribution}, FourthMoment, val, err)
```

Analytic expression for the no-central `FourthMoment` from a [`UniformDistribution`](@ref):

$$
M_4 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y^4 = x^4 + 2x^2\epsilon^2 + \frac{1}{5}\epsilon^4. 
$$
