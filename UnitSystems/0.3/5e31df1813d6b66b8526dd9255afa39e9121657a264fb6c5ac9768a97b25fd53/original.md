```Julia
molarmass(U::UnitSystem,S::UnitSystem) = molarmass(S)/molarmass(U)
molarmass(v::Real,U::UnitSystem,S::UnitSystem) = v/molarmass(U,S)
```

Molar mass or `mass` per `mole` (kg⋅mol⁻¹), unit conversion factor.

```Julia
julia> molarmass(CGS,Metric) # kg⋅g⁻¹
0.001

julia> molarmass(Metric,SI2019) # mol⋅mol⁻¹
0.9999999996562561
```
