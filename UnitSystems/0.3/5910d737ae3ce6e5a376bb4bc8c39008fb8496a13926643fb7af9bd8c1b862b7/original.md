```Julia
electricdisplacement(U::UnitSystem,S::UnitSystem) = charge(U,S)*rationalization(U,S)/area(U,S)
electricdisplacement(v::Real,U::UnitSystem,S::UnitSystem) = v/electricdisplacement(U,S)
```

Electric field displacement or surface `electricdisplacement` (C⋅m⁻²), unit conversion factor.

```Julia
julia> electricdisplacement(EMU,Metric) # C⋅cm²⋅abC⁻¹⋅m⁻²
7957.747154594764

julia> electricdisplacement(ESU,Metric) # C⋅cm²⋅statC⁻¹⋅m⁼²
2.654418729438071e-7

julia> electricdisplacement(Metric,SI2019) # C⋅C⁻¹
0.9999999997273952
```
