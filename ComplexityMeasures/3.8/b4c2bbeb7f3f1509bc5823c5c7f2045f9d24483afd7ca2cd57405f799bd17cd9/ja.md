```
Shannon <: InformationMeasure
Shannon(; base = 2)
```

シャノン [Shannon1948](@cite) エントロピーは、[`information`](@ref) と共に使用されて、次のように計算されます：

$$
H(p) = - \sum_i p[i] \log(p[i])
$$

ここで、$\log$ は指定された `base` で計算されます。

シャノンエントロピーの最大値は $\log_{base}(L)$ であり、$L$ は [`total_outcomes`](@ref) の一様分布のエントロピーです。
