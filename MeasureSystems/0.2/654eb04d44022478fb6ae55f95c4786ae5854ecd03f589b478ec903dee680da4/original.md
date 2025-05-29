```Julia
yank : [MLT⁻³], [FT⁻¹], [MLT⁻³], [MLT⁻³], [MLT⁻³]
yank(U::UnitSystem,S::UnitSystem) = mass(U,S)*jerk(U,S)
yank(v::Real,U::UnitSystem,S::UnitSystem) = v/yank(U,S)
MLT⁻³ [ħ⁻²𝘤⁵mₑ³ϕ⁻²g₀⁻²] Unified
```

Rate of change of `force` or `yank` (N⋅s⁻¹, kg⋅m⋅s⁻³), unit conversion factor.

```Julia
julia> yank(CGS,Metric) # N⋅dyn⁻¹
2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [kg⋅m]/[g⋅cm] Gauss -> Metric

julia> yank(CGS,English) # lb⋅dyn⁻¹
ft⁻¹lb⁻¹2⁻⁵5⁻⁵ = 7.233013851209893×10⁻⁵ [lbm⋅ft]/[g⋅cm] Gauss -> English

julia> yank(British,Metric) # N⋅lb⁻¹⋅
g₀⋅lb = 4.4482216152605 [kg⋅m]/[lb⋅s²] British -> Metric
```
