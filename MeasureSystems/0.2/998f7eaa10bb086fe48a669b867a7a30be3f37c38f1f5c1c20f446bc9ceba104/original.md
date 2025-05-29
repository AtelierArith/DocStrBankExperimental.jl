```Julia
frequency : [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹], [T⁻¹]
frequency(U::UnitSystem,S::UnitSystem) = 1/time(U,S)
frequency(v::Real,U::UnitSystem,S::UnitSystem) = v/frequency(U,S)
T⁻¹ [ħ⁻¹𝘤²mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Number of occurences per unit of time (Hz or s⁻¹), unit conversion factor.

```Julia
julia> frequency(IAU,Metric) day⋅s⁻¹
2⁻⁷3⁻³5⁻² = 1.1574074074074075×10⁻⁵ [Hz]/[D⁻¹] IAU☉ -> Metric
```
