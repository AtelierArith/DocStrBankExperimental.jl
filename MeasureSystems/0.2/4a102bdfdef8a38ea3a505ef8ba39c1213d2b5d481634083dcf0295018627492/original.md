```Julia
abvolt(U::UnitSystem) = electricpotential(𝟏,U,EMU)
electricpotential : [FLQ⁻¹], [FLQ⁻¹], [ML²T⁻²Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻²], [M¹ᐟ²L¹ᐟ²T⁻¹]
FLQ⁻¹⋅(𝘩⁻¹ᐟ²𝘤⁻³ᐟ²R∞⁻¹α²τ⁻¹2⁻⁶5⁻⁹ᐟ² = 6.4623785688(20) × 10⁻¹⁴) [ħ⁻¹ᐟ²𝘤⁵ᐟ²μ₀¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ¹ᐟ²αL⋅g₀⁻¹] Unified
```

Electromagnetic unit of `electricpotential` (V).

```Julia
julia> abvolt(Metric) # V
2⁻⁸5⁻⁸ = 1.0×10⁻⁸ [V] Metric

julia> abvolt(EMU) # abV
𝟏 = 1.0 [g¹ᐟ²cm³ᐟ²s⁻²] EMU

julia> abvolt(ESU) # statV
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g¹ᐟ²cm¹ᐟ²s⁻¹] ESU
```
