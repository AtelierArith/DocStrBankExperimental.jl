```Julia
force(U::UnitSystem,S::UnitSystem) = inertia(U,S)*acceleration(U,S)
force(v::Real,U::UnitSystem,S::UnitSystem) = v/force(U,S)
```

Weight or force or `inertia` times `acceleration` (N, kg⋅m⋅s⁻²), unit conversion factor.

```Julia
julia> force(CGS,Metric) # N⋅dyn⁻¹
1.0e-5

julia> force(CGS,English) # lb⋅dyn⁻¹
2.248089430997105e-6

julia> force(English,Metric) # N⋅lb⁻¹
4.4482216152605

julia> force(FPS,Metric) # pdl⋅N⁻¹
0.13825495437600002

julia> force(Engineering,Metric) # kp⋅N⁻¹
9.80665
```
