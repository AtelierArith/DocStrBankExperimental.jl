```Julia
reluctance(U::UnitSystem,S::UnitSystem) = rationalization(U,S)*lorentz(U,S)^2/inductance(U,S)
reluctance(v::Real,U::UnitSystem,S::UnitSystem) = v/reluctance(U,S)
```

Magnetic `reluctance` or magnetic resistance (H⁻¹, Gb⋅Mx⁻¹), unit conversion factor.

```Julia
julia> reluctance(EMU,Metric) # abH⋅H⁻¹
7.957747154594767e7

julia> reluctance(ESU,Metric) # statH⋅H⁻¹
8.854187817620388e-14

julia> reluctance(Metric,SI2019) # H⋅H⁻¹
0.9999999994547903
```
