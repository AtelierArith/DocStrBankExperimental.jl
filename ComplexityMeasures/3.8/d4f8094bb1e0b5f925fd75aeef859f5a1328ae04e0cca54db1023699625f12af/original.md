```
Curado <: InformationMeasure
Curado(; b = 1.0)
```

The Curado entropy [Curado2004](@cite), used with [`information`](@ref) to compute

$$
H_C(p) = \left( \sum_{i=1}^N e^{-b p_i} \right) + e^{-b} - 1,
$$

with `b ∈ ℛ, b > 0`, and the terms outside the sum ensures that $H_C(0) = H_C(1) = 0$.

The maximum entropy for `Curado` is $L(1 - \exp(-b/L)) + \exp(-b) - 1$ with $L$ the [`total_outcomes`](@ref).
