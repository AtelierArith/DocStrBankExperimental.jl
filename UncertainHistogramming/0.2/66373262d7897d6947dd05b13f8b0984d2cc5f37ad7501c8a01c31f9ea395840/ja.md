```
moment(::Type{GaussianDistribution}, FourthMoment, μ, σ)
```

非中心の `FourthMoment` の解析的表現は [`GaussianDistribution`](@ref) から得られます：

$$
M_4 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y^4 = \mu^4 + 6\mu^2\sigma^2 + 3\sigma^4. 
$$
