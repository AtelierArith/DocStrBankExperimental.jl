```
moment(::Type{GaussianDistribution}, FirstMoment, μ, σ)
```

非中心の `FirstMoment` の解析的表現は [`GaussianDistribution`](@ref) から次のようになります：

$$
M_1 = \int_{-\infty}^{\infty} {\rm d}y\, G(y;\mu,\sigma)\cdot y = \mu. 
$$
