```Julia
angulartime : [TA⁻¹], [T], [T], [T], [T]
angulartime(U::UnitSystem,S::UnitSystem) = time(U,S)/angle(U,S)
angulartime(v::Real,U::UnitSystem,S::UnitSystem) = v/angulartime(U,S)
TA⁻¹ [ħ⋅𝘤⁻²mₑ⁻¹g₀] Unified
```

Circular `time` per `angle` (s⋅rad⁻¹), unit conversion factor.

```Julia
julia> angulartime(IAU,Metric) s⋅day⁻¹
2⁷3³5² = 86400.0 [s]/[D] IAU☉ -> Metric
```
