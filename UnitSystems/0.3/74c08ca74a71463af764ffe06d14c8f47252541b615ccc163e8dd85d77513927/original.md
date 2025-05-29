```Julia
magneticpolarizability(U::UnitSystem,S::UnitSystem) = magneticdipolemoment(U,S)/magneticfield(U,S)
magneticpolarizability(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticpolarizability(U,S)
```

Polarizability or `magneticdipolemoment` per `magneticfield` (m³), unit conversion factor.

```Julia
julia> electricpolarizability(EMU,Metric) # m³⋅cm⁻³
100000.00000000004

julia> electricpolarizability(ESU,Metric) # m³⋅cm⁼³
1.1126500560536184e-16

julia> electricpolarizability(Metric,Gauss) # cm³⋅m⁻³
8.987551787368173e15

julia> electricpolarizability(Metric,SI2019)
0.9999999994547903
```
