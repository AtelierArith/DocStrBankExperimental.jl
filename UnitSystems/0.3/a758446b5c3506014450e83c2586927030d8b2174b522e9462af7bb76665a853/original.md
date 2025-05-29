```Julia
biotsavart(U::UnitSystem) = vacuumpermeability(U)*lorentz(U)*rationalization(U)/𝟐/τ
```

Magnetostatic proportionality constant `αB` for the Biot-Savart's law (H/m).

```Julia
julia> biotsavart(Metric) # H⋅m⁻¹
1.0000000000000001e-7

julia> biotsavart(CODATA) # H⋅m⁻¹
1.0000000003978213e-7

julia> biotsavart(SI2019) # H⋅m⁻¹
1.00000000054521e-7

julia> biotsavart(Conventional) # H⋅m⁻¹
9.999999827515425e-8

julia> biotsavart(International) # H⋅m⁻¹
9.995052449037728e-8

julia> biotsavart(InternationalMean) # H⋅m⁻¹
9.995102399824086e-8

julia> biotsavart(EMU) # abH⋅cm⁻¹
1.0

julia> biotsavart(ESU) # statH⋅cm⁻¹
1.1126500560536182e-21

julia> biotsavart(Gauss) # abH⋅cm⁻¹
3.335640951981521e-11

julia> biotsavart(HLU) # hlH⋅cm⁻¹
2.6544187294380728e-12
```
