```Julia
momentum : [MLT⁻¹], [FT], [MLT⁻¹], [MLT⁻¹], [MLT⁻¹]
momentum(U::UnitSystem,S::UnitSystem) = mass(U,S)*speed(U,S)
momentum(v::Real,U::UnitSystem,S::UnitSystem) = v/momentum(U,S)
MLT⁻¹ [𝘤⋅mₑ] Unified
```

Linear `momentum` or `mass` times `speed` (N⋅s, kg⋅m⋅s⁻¹), unit conversion factor.

```Julia
julia> momentum(CGS,Metric) # N⋅dyn⁻¹
2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [kg⋅m]/[g⋅cm] Gauss -> Metric

julia> momentum(CGS,English) # lb⋅dyn⁻¹
ft⁻¹lb⁻¹2⁻⁵5⁻⁵ = 7.233013851209893×10⁻⁵ [lbm⋅ft]/[g⋅cm] Gauss -> English

julia> momentum(British,Metric) # N⋅lb⁻¹
g₀⋅lb = 4.4482216152605 [kg⋅m]/[lb⋅s²] British -> Metric
```
