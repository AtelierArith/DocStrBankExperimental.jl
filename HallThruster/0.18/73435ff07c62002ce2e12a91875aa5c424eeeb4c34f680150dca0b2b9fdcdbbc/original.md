```
Gas(name, short_name; γ, M) -> Gas
```

Instantiate a new Gas, providing a name, short name, the adiabatic index, and the molar mass. Other gas properties, including gas constant, specific heats at constant pressure/volume, and mass of atom/molecule in kg will are then computed.

```jldoctest;setup = :(using HallThruster: Gas)
julia> Gas("Xenon", "Xe", γ = 5/3, M = 83.798)
Xenon
```
