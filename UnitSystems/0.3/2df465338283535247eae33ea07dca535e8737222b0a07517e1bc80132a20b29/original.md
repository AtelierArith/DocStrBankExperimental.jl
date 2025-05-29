```Julia
action(U::UnitSystem,S::UnitSystem) = energy(U,S)*time(U,S)
action(v::Real,U::UnitSystem,S::UnitSystem) = v/action(U,S)
```

Integrated `momentum` over `length` or `action` (J⋅s, N⋅m⋅s), unit conversion factor.

```Julia
julia> action(CGS,Metric) # J⋅erg⁻¹
1.0000000000000001e-7

julia> action(CGS,English) # ft⋅lb⋅erg⁻¹
7.375621492772652e-8

julia> action(English,Metric) # J⋅ft⁻¹⋅lb⁻¹
1.3558179483314003
```
