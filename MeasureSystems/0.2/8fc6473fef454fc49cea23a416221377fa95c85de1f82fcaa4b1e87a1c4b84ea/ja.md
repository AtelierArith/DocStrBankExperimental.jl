```Julia
angulartime : [TA⁻¹], [T], [T], [T], [T]
angulartime(U::UnitSystem,S::UnitSystem) = time(U,S)/angle(U,S)
angulartime(v::Real,U::UnitSystem,S::UnitSystem) = v/angulartime(U,S)
TA⁻¹ [ħ⋅𝘤⁻²mₑ⁻¹g₀] 統一

```

円周の `time` あたりの `angle` (s⋅rad⁻¹)、単位変換係数。

```Julia
julia> angulartime(IAU,Metric) s⋅day⁻¹
2⁷3³5² = 86400.0 [s]/[D] IAU☉ -> Metric
```
