```Julia
Planck = UnitSystem(𝟏,𝟏,𝟏,𝟏,√(𝟐*τ*αG))
```

Planck `UnitSystem` with the `electronmass` value `√(4π*αG)` using gravitational coupling.

```Julia
julia> boltzmann(Planck)
1

julia> planckreduced(Planck)
1

julia> lightspeed(Planck)
1

julia> vacuumpermeability(Planck)
1

julia> electronmass(Planck)
1.4837079572551133e-22
```
