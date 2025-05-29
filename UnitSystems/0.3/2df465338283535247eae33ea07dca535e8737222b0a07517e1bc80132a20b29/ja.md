```Julia
action(U::UnitSystem,S::UnitSystem) = energy(U,S)*time(U,S)
action(v::Real,U::UnitSystem,S::UnitSystem) = v/action(U,S)
```

`長さ` または `作用` (J⋅s, N⋅m⋅s) に対する `運動量` の統合、単位変換係数。

```Julia
julia> action(CGS,Metric) # J⋅erg⁻¹
1.0000000000000001e-7

julia> action(CGS,English) # ft⋅lb⋅erg⁻¹
7.375621492772652e-8

julia> action(English,Metric) # J⋅ft⁻¹⋅lb⁻¹
1.3558179483314003
```
