```
moment(::Type{GaussianDistribution}, ThirdMoment, μ, σ)
```

非中心の `ThirdMoment` の解析的表現は [`GaussianDistribution`](@ref) から得られます：

$$
M_3 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y^3 = \mu^3 + 3\mu\sigma^2. 
$$
