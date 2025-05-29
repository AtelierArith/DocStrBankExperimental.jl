```Julia
frequencydrift : [T⁻²], [T⁻²], [T⁻²], [T⁻²], [T⁻²]
frequencydrift(U::UnitSystem,S::UnitSystem) = 1/time(U,S)^2
frequencydrift(v::Real,U::UnitSystem,S::UnitSystem) = v/frequencydrift(U,S)
T⁻² [ħ⁻²𝘤⁴mₑ²ϕ⁻²g₀⁻²] 統一

`frequency` の `time` あたりのドリフトまたは `frequencydrift` (Hz⋅s⁻¹, s⁻²)、単位変換係数。

```

Julia julia> frequencydrift(IAU,Metric) day²⋅Hz⋅s⁻¹ 2⁻¹⁴3⁻⁶5⁻⁴ = 1.3395919067215363×10⁻¹⁰ [Hz⋅s⁻¹]/[D⁻²] IAU☉ -> Metric ```
