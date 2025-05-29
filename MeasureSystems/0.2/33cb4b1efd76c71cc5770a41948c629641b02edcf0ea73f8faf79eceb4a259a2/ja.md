```Julia
crackle : [LT⁻⁵], [LT⁻⁵], [LT⁻⁵], [LT⁻⁵], [LT⁻⁵]
crackle(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^4
crackle(v::Real,U::UnitSystem,S::UnitSystem) = v/crackle(U,S)
LT⁻⁵ [ħ⁻⁴𝘤⁹mₑ⁴ϕ⁻⁴g₀⁻⁴] 統一

A `snap` per `time` or `crackle` (m⋅s⁻⁵), 単位変換係数。

```

Julia julia> crackle(CGS,Metric) # m⋅cm⁻¹ 2⁻²5⁻² = 0.010000000000000002 [m]/[cm] Gauss -> Metric

julia> crackle(IAU,Metric) # m⋅day⁵⋅s⁻⁵⋅au⁻¹ au⋅2⁻³⁵3⁻¹⁵5⁻¹⁰ = 3.107110507521(62) × 10⁻¹⁴ [m⋅s⁻⁵]/[au⋅D⁻⁵] IAU☉ -> Metric

julia> crackle(English,Metric) # m⋅ft⁻¹ ft = 0.3048 [m]/[ft] English -> Metric

julia> crackle(Survey,English) # ft⋅ftUS⁻¹ ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] Survey -> English ```
