```
Curado <: InformationMeasure
Curado(; b = 1.0)
```

Curadoエントロピー [Curado2004](@cite) は、[`information`](@ref) と共に使用されて計算されます。

$$
H_C(p) = \left( \sum_{i=1}^N e^{-b p_i} \right) + e^{-b} - 1,
$$

ここで `b ∈ ℛ, b > 0` であり、合計の外の項は $H_C(0) = H_C(1) = 0$ を保証します。

`Curado` の最大エントロピーは $L(1 - \exp(-b/L)) + \exp(-b) - 1$ であり、$L$ は [`total_outcomes`](@ref) です。
