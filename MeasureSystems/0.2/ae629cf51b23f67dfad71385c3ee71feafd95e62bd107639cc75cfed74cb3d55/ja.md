```Julia
speed : [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹], [LT⁻¹]
speed(U::UnitSystem,S::UnitSystem) = lightspeed(S)/lightspeed(U)
speed(v::Real,U::UnitSystem,S::UnitSystem) = v/speed(U,S)
LT⁻¹ [𝘤] 統一

速度または `長さ` あたりの `時間` または `速度` (m⋅s⁻¹)、単位変換係数。

```

Julia julia> speed(CGS,Metric) # m⋅cm⁻¹ 2⁻²5⁻² = 0.010000000000000002 [m]/[cm] ガウス -> メトリック

julia> speed(IAU,Metric) # m⋅day⋅s⁻¹⋅au⁻¹ au⋅2⁻⁷3⁻³5⁻² = 1.731456836806(35) × 10⁶ [m⋅s⁻¹]/[au⋅D⁻¹] IAU☉ -> メトリック

julia> speed(English,Metric) # m⋅ft⁻¹ ft = 0.3048 [m]/[ft] 英語 -> メトリック

julia> speed(Survey,English) # ft⋅ftUS⁻¹ ft⁻¹ftUS = 1.0000020000039997 [ft]/[ft] 調査 -> 英語 ```
