```Julia
molaramount(U::UnitSystem,S::UnitSystem) = mass(U,S)*molality(U,S)
molaramount(v::Real,U::UnitSystem,S::UnitSystem) = v/molaramount(U,S)
```

Amount of molecular substance or `molaramount` (mol), unit conversion factor.

```Julia
julia> molaramount(SI2019,Metric) # mol⋅mol⁻¹
0.9999999996562561

julia> molaramount(British,SI2019) # mol⋅slug-mol⁻¹
453.59237015591964

julia> molaramount(English,SI2019) # mol⋅lb-mol⁻¹
453.59237015591964
```
