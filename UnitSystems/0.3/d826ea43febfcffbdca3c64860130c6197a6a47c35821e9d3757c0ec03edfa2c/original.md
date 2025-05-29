```Julia
magneticfield(U::UnitSystem,S::UnitSystem) = current(U,S)*rationalization(U,S)*lorentz(U,S)/length(U,S)
magneticfield(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticfield(U,S)
```

Magnetization or `magneticfield` or `current` per `length` (A⋅m⁻¹), unit conversion factor.

```Julia
julia> magneticfield(EMU,Metric) # A⋅m⁻¹⋅Oe⁻¹
79.57747154594766

julia> magneticfield(ESU,Metric) # A⋅cm⋅m⁻¹⋅statA⁻¹
2.6544187294380718e-9

julia> magneticfield(Metric,SI2019) # A⋅A⁻¹
0.9999999997273952
```
