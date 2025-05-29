```Julia
angularmomentum(U::UnitSystem,S::UnitSystem) = impulse(U,S)*length(U,S)/angle(U,S)
angularmomentum(v::Real,U::UnitSystem,S::UnitSystem) = v/angularmomentum(U,S)
```

回転モーメントまたは `angularmomentum` (N⋅m⋅s, kg⋅m²⋅s⁻¹)、単位変換係数。

```Julia
julia> momentum(CGS,Metric) # N⋅m⋅dyn⁻¹⋅cm⁻¹
1.0e-5

julia> momentum(CGS,English) # lb⋅ft⋅dyn⁻¹⋅cm⁻¹
7.233013851209893e-5

julia> momentum(British,Metric) # N⋅m⋅lb⁻¹⋅ft⁻¹
4.4482216152605
```
