```Julia
specificenergy(U::UnitSystem,S::UnitSystem) = speed(U,S)^2/gravity(U,S)
specificenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/specificenergy(U,S)
```

Massic energy or `energy` per `mass` or `specificenergy` (J⋅kg⁻¹), unit conversion factor.

```Julia
julia> specificenergy(CGS,Metric) # m²⋅cm⁻²
0.0001

julia> specificenergy(IAU,Metric) # m²⋅day²⋅s⁻²⋅au⁻²
2.9979427777207e12

julia> specificenergy(English,Metric) # m²⋅ft⁻²
2.98906692

julia> specificenergy(Survey,English) # ft²⋅ftUS⁻²
1.000002000004
```
