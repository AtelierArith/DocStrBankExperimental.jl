```Julia
momentum(U::UnitSystem,S::UnitSystem) = mass(U,S)*speed(U,S)
momentum(v::Real,U::UnitSystem,S::UnitSystem) = v/momentum(U,S)
```

線形 `momentum` または `mass` と `speed` の積 (N⋅s, kg⋅m⋅s⁻¹)、単位換算係数。

```Julia
julia> momentum(CGS,Metric) # N⋅dyn⁻¹
1.0e-5

julia> momentum(CGS,English) # lb⋅dyn⁻¹
7.233013851209893e-5

julia> momentum(British,Metric) # N⋅lb⁻¹
4.4482216152605
```
