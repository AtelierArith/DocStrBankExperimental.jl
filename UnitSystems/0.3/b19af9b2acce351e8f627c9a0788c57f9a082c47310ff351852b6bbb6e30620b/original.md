```Julia
molarenergy(U::UnitSystem,S::UnitSystem) = energy(U,S)/molaramount(U,S)
molarenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/molarenergy(U,S)
```

Gibbs free `energy` per `mole` or `molarenergy` (J⋅mol⁻¹), unit conversion factor.

```Julia
julia> molarenergy(CGS,Metric) # J⋅erg⁻¹
1.0000000000000001e-7

julia> molarenergy(English,SI2019) # J⋅slug-mol⋅ft⁻¹⋅lb⁻¹⋅mol⁻¹
0.002989066918972526
```
