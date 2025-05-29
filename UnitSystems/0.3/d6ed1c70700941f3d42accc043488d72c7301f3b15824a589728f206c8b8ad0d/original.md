```Julia
electrostatic(U::UnitSystem) = rationalization(U)/𝟐/τ/vacuumpermittivity(U)
```

Electrostatic proportionality constant `kₑ` for the Coulomb's law force (N⋅m²⋅C⁻²).

```Julia
julia> electrostatic(Metric) # N⋅m²⋅C⁻²
8.987551787368177e9

julia> electrostatic(CODATA) # N·m²⋅C⁻²
8.987551790943615e9

julia> electrostatic(SI2019) # N·m²⋅C⁻²
8.98755179226828e9

julia> electrostatic(Conventional) # N·m²⋅C⁻²
8.98755163234677e9

julia> electrostatic(International) # N·m²⋅C⁻²
8.98310515031877e9

julia> electrostatic(EMU) # dyn⋅cm²⋅abC⁻²
8.987551787368177e20

julia> electrostatic(ESU) # dyn⋅cm²⋅statC⁻²
0.9999999999999998

julia> electrostatic(HLU) # dyn⋅cm²⋅hlC⁻²
0.07957747154594767
```
