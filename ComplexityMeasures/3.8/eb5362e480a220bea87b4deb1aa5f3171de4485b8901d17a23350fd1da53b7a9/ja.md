```
Kaniadakis <: InformationMeasure
Kaniadakis(; κ = 1.0, base = 2.0)
```

Kaniadakisエントロピー [Tsallis2009](@cite) は、[`information`](@ref) と共に使用されて計算されます。

$$
H_K(p) = -\sum_{i=1}^N p_i f_\kappa(p_i),
$$

$$
f_\kappa (x) = \dfrac{x^\kappa - x^{-\kappa}}{2\kappa},
$$

ここで、$\kappa = 0$ の場合は、指定された `base` に対して通常の対数が使用され、0の確率はスキップされます。
