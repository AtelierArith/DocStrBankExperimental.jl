```
moment(::Type{UniformDistribution}, FirstMoment, val, err)
```

非中心の `FirstMoment` の解析的表現は [`UniformDistribution`](@ref) から次のようになります：

$$
M_1 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y = x. 
$$
