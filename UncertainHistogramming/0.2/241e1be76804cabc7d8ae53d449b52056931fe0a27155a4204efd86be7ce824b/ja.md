```
moment(::Type{UniformDistribution}, ThirdMoment, val, err)
```

非中心の `ThirdMoment` の解析的表現は [`UniformDistribution`](@ref) から次のようになります：

$$
M_3 = \int_{-\infty}^{\infty} {\rm d}y\, \mathcal{U}(y; x, \epsilon)\cdot y^3 = x\left(x^2 + \epsilon^2 \right). 
$$
