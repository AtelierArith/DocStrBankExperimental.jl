```Julia
加速度 : [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²]
加速度(U::UnitSystem,S::UnitSystem) = 速度(U,S)/時間(U,S)
加速度(v::Real,U::UnitSystem,S::UnitSystem) = v/加速度(U,S)
LT⁻² [ħ⁻¹𝘤³mₑ⋅ϕ⁻¹g₀⁻¹] 統一

特定の力または `速度` あたりの `時間` または `加速度` (m⋅s⁻²)、単位換算係数。

```

Julia julia> 加速度(CGS,Metric) # m⋅s⁻¹⋅gal⁻¹ 2⁻²5⁻² = 0.010000000000000002 [m]/[cm] ガウス -> メトリック

julia> 加速度(IAU,Metric) # m⋅day²⋅s⁻²⋅au⁻¹ au⋅2⁻¹⁴3⁻⁶5⁻⁴ = 20.0400096852500(40) [m⋅s⁻²]/[au⋅D⁻²] IAU☉ -> メトリック

julia> 加速度(English,Metric) # m⋅ft⁻¹ ft = 0.3048 [m]/[ft] 英語 -> メトリック

julia> 加速度(Survey,English) # ft⋅ftUS⁻¹ ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] 調査 -> 英語 ```
