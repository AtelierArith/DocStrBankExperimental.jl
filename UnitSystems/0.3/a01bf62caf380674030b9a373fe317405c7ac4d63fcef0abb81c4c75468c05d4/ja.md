```Julia
vacuumpermeability(U::UnitSystem) = 𝟏/vacuumpermittivity(U)/(lightspeed(U)*lorentz(U))^2
```

古典真空における磁気透過率は、SI単位系（H⋅m⁻¹, kg⋅m²⋅C⁻²）で `μ₀` として定義されます。

```Julia
julia> vacuumpermeability(Metric) # H⋅m⁻¹
1.2566370614359173e-6

julia> vacuumpermeability(Conventional) # H⋅m⁻¹
1.2566370397608662e-6

julia> vacuumpermeability(CODATA) # H⋅m⁻¹
1.2566370619358342e-6

julia> vacuumpermeability(SI2019) # H⋅m⁻¹
1.256637062121048e-6

julia> vacuumpermeability(International) # H⋅m⁻¹
1.2560153338456639e-6

julia> vacuumpermeability(EMU) # abH⋅cm⁻¹
1

julia> vacuumpermeability(ESU) # statH⋅cm⁻¹
1.1126500560536182e-21
```
