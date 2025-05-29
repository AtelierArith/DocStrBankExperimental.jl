```
moment(::Type{UniformDistribution}, SecondMoment, val, err)
```

非中心の `SecondMoment` の解析的表現は [`UniformDistribution`](@ref) から得られます：

$$
M_2 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y^2 = x^2 + \frac{1}{3}\epsilon^2. 
$$
