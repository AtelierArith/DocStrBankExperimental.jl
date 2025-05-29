```Julia
volt(U::UnitSystem) = electricpotential(𝟏,U,Metric)
electricpotential : [FLQ⁻¹], [FLQ⁻¹], [ML²T⁻²Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻²], [M¹ᐟ²L¹ᐟ²T⁻¹]
FLQ⁻¹⋅(𝘩⁻¹ᐟ²𝘤⁻³ᐟ²R∞⁻¹α²τ⁻¹2²5⁷ᐟ² = 6.4623785688(20) × 10⁻⁶) [ħ⁻¹ᐟ²𝘤⁵ᐟ²μ₀¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ¹ᐟ²αL⋅g₀⁻¹] Unified
```

Metric unit of `electricpotential` (V).

```Julia
julia> volt(Metric) # V
𝟏 = 1.0 [V] Metric

julia> volt(EMU) # abV
2⁸5⁸ = 1.0×10⁸ [g¹ᐟ²cm³ᐟ²s⁻²] EMU

julia> volt(ESU) # statV
𝘤⁻¹2⁶5⁶ = 0.0033356409519815205 [g¹ᐟ²cm¹ᐟ²s⁻¹] ESU
```
