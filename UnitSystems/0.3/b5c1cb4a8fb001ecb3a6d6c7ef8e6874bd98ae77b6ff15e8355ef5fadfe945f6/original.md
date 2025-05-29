```Julia
power(U::UnitSystem,S::UnitSystem) = energy(U,S)/time(U,S))
power(v::Real,U::UnitSystem,S::UnitSystem) = v/power(U,S)
```

Radiant flux or `power` or `energy` per `time` (W, J⋅s⁻¹, kg⋅m²⋅s⁻³), unit conversion factor.

```Julia
julia> power(CGS,Metric) # W⋅s⋅erg⁻¹
1.0000000000000001e-7

julia> power(English,Metric) # W⋅s⋅ft⁻¹⋅lb⁻¹
1.3558179483314003
```
