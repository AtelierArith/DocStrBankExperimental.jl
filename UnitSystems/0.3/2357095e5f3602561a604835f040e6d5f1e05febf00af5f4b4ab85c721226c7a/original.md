```Julia
electricfield(U::UnitSystem,S::UnitSystem) = electricpotential(U,S)/length(U,S)
electricfield(v::Real,U::UnitSystem,S::UnitSystem) = v/electricfield(U,S)
```

The `electricpotential` per `length` or `electricfield` (V⋅m⁻¹), unit conversion factor.

```Julia
julia> electricfield(EMU,Metric) # V⋅cm⋅abV⁻¹⋅m⁻¹
9.999999999999997e-7

julia> electricfield(EMU,ESU) # statV⋅abV⁻¹
3.33564095198152e-11

julia> electricfield(ESU,Metric) # V⋅cm⋅statV⁻¹⋅m⁻¹
29979.2458

julia> electricfield(Metric,SI2019) # V⋅V⁻¹
1.0000000002726048
```
