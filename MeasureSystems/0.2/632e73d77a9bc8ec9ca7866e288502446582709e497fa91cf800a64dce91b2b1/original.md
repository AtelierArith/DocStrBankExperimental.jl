```Julia
frequencydrift : [T⁻²], [T⁻²], [T⁻²], [T⁻²], [T⁻²]
frequencydrift(U::UnitSystem,S::UnitSystem) = 1/time(U,S)^2
frequencydrift(v::Real,U::UnitSystem,S::UnitSystem) = v/frequencydrift(U,S)
T⁻² [ħ⁻²𝘤⁴mₑ²ϕ⁻²g₀⁻²] Unified
```

Drift of `frequency` per `time` or `frequencydrift` (Hz⋅s⁻¹, s⁻²), unit conversion factor.

```Julia
julia> frequencydrift(IAU,Metric) day²⋅Hz⋅s⁻¹
2⁻¹⁴3⁻⁶5⁻⁴ = 1.3395919067215363×10⁻¹⁰ [Hz⋅s⁻¹]/[D⁻²] IAU☉ -> Metric
```
