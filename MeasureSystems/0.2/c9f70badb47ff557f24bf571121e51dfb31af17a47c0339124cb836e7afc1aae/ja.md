```Julia
snap : [LT⁻⁴], [LT⁻⁴], [LT⁻⁴], [LT⁻⁴], [LT⁻⁴]
snap(U::UnitSystem,S::UnitSystem) = speed(U,S)/time(U,S)^3
snap(v::Real,U::UnitSystem,S::UnitSystem) = v/snap(U,S)
LT⁻⁴ [ħ⁻³𝘤⁷mₑ³ϕ⁻³g₀⁻³] 統一

ジャウンスまたは `ジャーク` あたりの `時間` または `スナップ` (m⋅s⁻⁴)、単位換算係数。

```

Julia julia> snap(CGS,Metric) # m⋅cm⁻¹ 2⁻²5⁻² = 0.010000000000000002 [m]/[cm] ガウス -> メトリック

julia> snap(IAU,Metric) # m⋅day⁴⋅s⁻⁴⋅au⁻¹ au⋅2⁻²⁸3⁻¹²5⁻⁸ = 2.684543478498(54) × 10⁻⁹ [m⋅s⁻⁴]/[au⋅D⁻⁴] IAU☉ -> メトリック

julia> snap(English,Metric) # m⋅ft⁻¹ ft = 0.3048 [m]/[ft] 英語 -> メトリック

julia> snap(Survey,English) # ft⋅ftUS⁻¹ ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] サーベイ -> 英語 ```
