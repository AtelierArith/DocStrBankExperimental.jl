```Julia
Electronic = UnitSystem(𝟏,𝟏/α,𝟏,𝟐*τ,𝟏)
```

Electronic `UnitSystem` with `planckreduced` of `1/α` and `permeability` of `4π`.

```Julia
julia> boltzmann(Electronic)
1

julia> planckreduced(Electronic)
137.035999084

julia> lightspeed(Electronic)
1

julia> vacuumpermeability(Electronic)
12.566370614359172

julia> electronmass(Electronic)
1
```
