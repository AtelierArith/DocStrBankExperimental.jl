```
moment(::Type{UniformDistribution}, FourthMoment, val, err)
```

非中心の `FourthMoment` の解析的表現は [`UniformDistribution`](@ref) から得られます：

$$
M_4 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y^4 = x^4 + 2x^2\epsilon^2 + \frac{1}{5}\epsilon^4. 
$$
