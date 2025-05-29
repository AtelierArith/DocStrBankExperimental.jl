```Julia
hertz(U::UnitSystem) = 𝟏/second(U)
frequency : [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹⋅(𝘤⁻¹R∞⁻¹α²τ⁻¹2⁻¹ = 1.28808866819(39) × 10⁻²¹) [ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Metric unit of `frequency` (s⁻¹).

```Julia
julia> hertz(Engineering) # rad⋅s⁻¹
𝟏 = 1.0 [Hz] Engineering

julia> hertz(IAU) # D⁻¹
2⁷3³5² = 86400.0 [D⁻¹] IAU☉
```
