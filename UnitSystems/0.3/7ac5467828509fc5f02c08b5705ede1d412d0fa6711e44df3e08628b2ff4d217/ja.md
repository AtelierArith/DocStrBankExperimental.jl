```Julia
yank(U::UnitSystem,S::UnitSystem) = mass(U,S)*jerk(U,S)
yank(v::Real,U::UnitSystem,S::UnitSystem) = v/yank(U,S)
```

`force` または `yank` の変化率 (N⋅s⁻¹, kg⋅m⋅s⁻³)、単位変換係数。

```Julia
julia> yank(CGS,Metric) # N⋅dyn⁻¹
1.0e-5

julia> yank(CGS,English) # lb⋅dyn⁻¹
7.233013851209893e-5

julia> yank(British,Metric) # N⋅lb⁻¹⋅
4.4482216152605
```
