```Julia
momentum : [MLT⁻¹], [FT], [MLT⁻¹], [MLT⁻¹], [MLT⁻¹]
momentum(U::UnitSystem,S::UnitSystem) = mass(U,S)*speed(U,S)
momentum(v::Real,U::UnitSystem,S::UnitSystem) = v/momentum(U,S)
MLT⁻¹ [𝘤⋅mₑ] 統一

線形 `momentum` または `mass` と `speed` (N⋅s, kg⋅m⋅s⁻¹)、単位換算係数。

```

Julia julia> momentum(CGS,Metric) # N⋅dyn⁻¹ 2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [kg⋅m]/[g⋅cm] ガウス -> メトリック

julia> momentum(CGS,English) # lb⋅dyn⁻¹ ft⁻¹lb⁻¹2⁻⁵5⁻⁵ = 7.233013851209893×10⁻⁵ [lbm⋅ft]/[g⋅cm] ガウス -> 英語

julia> momentum(British,Metric) # N⋅lb⁻¹ g₀⋅lb = 4.4482216152605 [kg⋅m]/[lb⋅s²] ブリティッシュ -> メトリック ```
