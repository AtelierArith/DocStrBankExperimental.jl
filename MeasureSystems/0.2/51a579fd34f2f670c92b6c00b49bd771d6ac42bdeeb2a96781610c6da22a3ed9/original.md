```Julia
apm(U::UnitSystem) = 𝟏/minute(U)
frequency : [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹⋅(𝘤⁻¹R∞⁻¹α²τ⁻¹2⁻³3⁻¹5⁻¹ = 2.14681444698(66) × 10⁻²³) [ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Actions per minute `apm` unit of `frequency` (s⁻¹).

```Julia
julia> apm(Metric) # s⁻¹
2⁻²3⁻¹5⁻¹ = 0.016666666666666666 [Hz] Metric

julia> apm(MPH) # h⁻¹
2²3⋅5 = 60.0 [h⁻¹] MPH

julia> apm(IAU) # D⁻¹
2⁵3²5 = 1440.0 [D⁻¹] IAU☉
```
