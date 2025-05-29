```
moment(::Type{GaussianDistribution}, SecondMoment, μ, σ)
```

非中心の `SecondMoment` の解析的表現は [`GaussianDistribution`](@ref) から得られます：

$$
M_2 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y^2 = \mu^2 + \sigma^2. 
$$
