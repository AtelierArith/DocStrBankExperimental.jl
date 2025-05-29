```Julia
conductance(U::UnitSystem,S::UnitSystem) = current(U,S)/electricpotential(U,S)
conductance(v::Real,U::UnitSystem,S::UnitSystem) = v/conductance(U,S)
```

Electrical `conductance` or `current` per `electricpotential` (S, Ω⁻¹, A⋅V⁻¹), unit conversion factor.

```Julia
julia> conductance(EMU,Metric) # S⋅abS⁻¹
1.0e9

julia> conductance(ESU,Metric) # S⋅statS⁻¹
1.112650056053618e-12

julia> conductance(Metric,SI2019) # S⋅S⁻¹
0.9999999994547903
```
