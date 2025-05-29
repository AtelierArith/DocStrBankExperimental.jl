```Julia
radiantintensity(U::UnitSystem,S::UnitSystem) = power(U,S)/solidangle(U,S)
radiantintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/radiantintensity(U,S)
```

Radiant intensity or `power` per `solidangle` (W⋅sr⁻¹, W⋅rad⁻²), unit conversion factor.

```Julia
julia> radiantintensity(CGS,Metric) # W⋅s⋅erg⁻¹
1.0000000000000001e-7

julia> radiantintensity(English,Metric) # W⋅s⋅ft⁻¹⋅lb⁻¹
1.3558179483314003
```
