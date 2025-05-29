```Julia
curie(U::UnitSystem) = frequency(𝟏,U,Metric)
frequency : [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
T⁻¹⋅37 [ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Reference unit of radioactivity (Bq or s⁻¹).

```Julia
julia> curie(Metric) # Bq
2⁹5⁹⋅37 = 3.7×10¹⁰ [Hz] Metric

julia> curie(IAU) # D⁻¹
2¹⁶3³5¹¹⋅37 = 3.1968×10¹⁵ [D⁻¹] IAU☉
```
