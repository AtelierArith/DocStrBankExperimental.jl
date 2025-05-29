```Julia
catalysis(U::UnitSystem,S::UnitSystem) = molaramount(U,S)/time(U,S)
catalysis(v::Real,U::UnitSystem,S::UnitSystem) = v/catalysis(U,S)
```

Catalytic activity or `molaramount` per `time` (kat, mol⋅s⁻¹), unit conversion factor.

```Julia
julia> catalysis(English,Metric) # kat⋅s⋅lb-mol⁻¹
453.59237
```
