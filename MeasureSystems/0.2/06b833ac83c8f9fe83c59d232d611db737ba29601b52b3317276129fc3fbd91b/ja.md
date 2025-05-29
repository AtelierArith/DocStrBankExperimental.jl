```Julia
ジャーク : [LT⁻³], [LT⁻³], [LT⁻³], [LT⁻³], [LT⁻³]
ジャーク(U::UnitSystem,S::UnitSystem) = スピード(U,S)/時間(U,S)^2
ジャーク(v::Real,U::UnitSystem,S::UnitSystem) = v/ジャーク(U,S)
LT⁻³ [ħ⁻²𝘤⁵mₑ²ϕ⁻²g₀⁻²] 統一

```

Julia julia> ジャーク(CGS,Metric) # m⋅cm⁻¹ 2⁻²5⁻² = 0.010000000000000002 [m]/[cm] ガウス -> メトリック

julia> ジャーク(IAU,Metric) # m⋅day³⋅s⁻³⋅au⁻¹ au⋅2⁻²¹3⁻⁹5⁻⁶ = 0.0002319445565422(47) [m⋅s⁻³]/[au⋅D⁻³] IAU☉ -> メトリック

julia> ジャーク(English,Metric) # m⋅ft⁻¹ ft = 0.3048 [m]/[ft] 英語 -> メトリック

julia> ジャーク(Survey,English) # ft⋅ftUS⁻¹ ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] サーベイ -> 英語 ```
