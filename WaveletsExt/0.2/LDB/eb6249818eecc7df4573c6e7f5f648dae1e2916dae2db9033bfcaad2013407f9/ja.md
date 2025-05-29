```
ProbabilityDensity <: EnergyMap
```

確率密度に基づくエネルギーマップであり、$Z_i$のpdfの違いに基づく測定です。係数の真の密度関数がわからないため、PDFは平均シフトヒストグラム（ASH）を使用して推定されます。

**参照:** [`EnergyMap`](@ref), [`TimeFrequency`](@ref), [`Signatures`](@ref)
