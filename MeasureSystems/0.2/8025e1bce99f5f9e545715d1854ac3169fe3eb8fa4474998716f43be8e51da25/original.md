```Julia
force : [F], [F], [MLT⁻²], [MLT⁻²], [MLT⁻²]
force(U::UnitSystem,S::UnitSystem) = inertia(U,S)*acceleration(U,S)
force(v::Real,U::UnitSystem,S::UnitSystem) = v/force(U,S)
F [ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] Unified
```

Weight or force or `inertia` times `acceleration` (N, kg⋅m⋅s⁻²), unit conversion factor.

```Julia
julia> force(CGS,Metric) # N⋅dyn⁻¹
2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [N]/[dyn] Gauss -> Metric

julia> force(CGS,English) # lb⋅dyn⁻¹
g₀⁻¹lb⁻¹2⁻⁵5⁻⁵ = 2.248089430997105×10⁻⁶ [lbf]/[dyn] Gauss -> English

julia> force(English,Metric) # N⋅lb⁻¹
g₀⋅lb = 4.4482216152605 [N]/[lbf] English -> Metric

julia> force(FPS,Metric) # pdl⋅N⁻¹
ft⋅lb = 0.13825495437600002 [N]/[pdl] FPS -> Metric

julia> force(Engineering,Metric) # kp⋅N⁻¹
g₀ = 9.80665 [N]/[kgf] Engineering -> Metric
```
