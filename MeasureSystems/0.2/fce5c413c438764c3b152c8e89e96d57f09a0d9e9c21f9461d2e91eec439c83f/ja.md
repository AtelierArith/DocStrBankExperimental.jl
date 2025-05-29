```Julia
hyperfine(U::UnitSystem) = frequency(ΔνCs = 9.19263177×10⁹,U)
frequency : [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹⋅(𝘤⁻¹ΔνCs⋅R∞⁻¹α²τ⁻¹2⁻¹ = 1.18409248138(36) × 10⁻¹¹) [ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

セシウム-133原子の非摂動基底状態ハイパーファイン遷移周波数 `ΔνCs` (Hz)。

```Julia
julia> hyperfine(Metric) # Hz
ΔνCs = 9.19263177×10⁹ [Hz] Metric
```
