```Julia
angularmomentum : [FLTA⁻¹], [FLT], [ML²T⁻¹], [ML²T⁻¹], [ML²T⁻¹]
angularmomentum(U::UnitSystem,S::UnitSystem) = impulse(U,S)*length(U,S)/angle(U,S)
angularmomentum(v::Real,U::UnitSystem,S::UnitSystem) = v/angularmomentum(U,S)
FLTA⁻¹ [ħ] 統一

回転モーメントまたは `angularmomentum` (N⋅m⋅s, kg⋅m²⋅s⁻¹)、単位変換係数。

```

Julia julia> momentum(CGS,Metric) # N⋅m⋅dyn⁻¹⋅cm⁻¹ 2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [kg⋅m]/[g⋅cm] ガウス -> メトリック

julia> momentum(CGS,English) # lb⋅ft⋅dyn⁻¹⋅cm⁻¹ ft⁻¹lb⁻¹2⁻⁵5⁻⁵ = 7.233013851209893×10⁻⁵ [lbm⋅ft]/[g⋅cm] ガウス -> 英語

julia> momentum(British,Metric) # N⋅m⋅lb⁻¹⋅ft⁻¹ g₀⋅lb = 4.4482216152605 [kg⋅m]/[lb⋅s²] ブリティッシュ -> メトリック ```
