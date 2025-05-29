```Julia
linearchargedensity(U::UnitSystem,S::UnitSystem) = charge(U,S)/length(U,S)
linearchargedensity(v::Real,U::UnitSystem,S::UnitSystem) = v/linearchargedensity(U,S)
```

Amount of `linearchargedensity` or `charge` per `length` (C⋅m⁻¹), unit conversion factor.

```Julia
julia> linearchargedensity(EMU,Metric) # C⋅cm⋅abC⁻¹⋅m⁻¹
999.9999999999998

julia> linearchargedensity(ESU,Metric) # C⋅cm⋅statC⁻¹⋅m⁼¹
3.33564095198152e-8

julia> linearchargedensity(Metric,SI2019) # C⋅C⁻¹
0.9999999997273952
```
