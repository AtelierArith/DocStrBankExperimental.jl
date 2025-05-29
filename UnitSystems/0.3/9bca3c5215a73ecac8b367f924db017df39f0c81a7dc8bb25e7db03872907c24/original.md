```Julia
capacitance(U::UnitSystem,S::UnitSystem) = charge(U,S)/electricpotential(U,S)
capacitance(v::Real,U::UnitSystem,S::UnitSystem) = v/capacitance(U,S)
```

Electrical `capactiance` or `charge` per `electricpotential` (F, C⋅V⁻¹), unit conversion factor.

```Julia
julia> capacitance(EMU,Metric) # F⋅abF⁻¹
1.0e9

julia> capacitance(ESU,Metric) # F⋅cm⁻¹
1.112650056053618e-12

julia> capactiance(Metric,SI2019) # F⋅F⁻¹
0.9999999994547903
```
