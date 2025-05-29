```Julia
inductance(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)/current(U,S)
inductance(v::Real,U::UnitSystem,S::UnitSystem) = v/inductance(U,S)
```

Electro-`magneticflux` per `current` or `inductance` (H, Ω⋅s, Wb⋅A⁻¹), unit conversion factor.

```Julia
julia> inductance(EMU,Metric) # H⋅abH⁻¹
1.0e-9

julia> inductance(ESU,Metric) # H⋅statH⁻¹
8.987551787368179e11

julia> inductance(Metric,SI2019) # H⋅H⁻¹
1.0000000005452097
```
