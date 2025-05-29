```Julia
yank(U::UnitSystem,S::UnitSystem) = mass(U,S)*jerk(U,S)
yank(v::Real,U::UnitSystem,S::UnitSystem) = v/yank(U,S)
```

Rate of change of `force` or `yank` (N⋅s⁻¹, kg⋅m⋅s⁻³), unit conversion factor.

```Julia
julia> yank(CGS,Metric) # N⋅dyn⁻¹
1.0e-5

julia> yank(CGS,English) # lb⋅dyn⁻¹
7.233013851209893e-5

julia> yank(British,Metric) # N⋅lb⁻¹⋅
4.4482216152605
```
