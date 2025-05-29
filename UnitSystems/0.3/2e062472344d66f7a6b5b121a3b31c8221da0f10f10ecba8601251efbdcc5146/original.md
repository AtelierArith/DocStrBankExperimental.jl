```Julia
Schrodinger = UnitSystem(𝟏,𝟏,𝟏/α,𝟐*τ*α^2,√(αG/α))
```

Schrodinger `UnitSystem` with `permeability` of `4π/αinv^2` and `electronmass` of `√(αG*αinv)`.

```Julia
julia> boltzmann(Schrodinger)
1

julia> planckreduced(Schrodinger)
1

julia> lightspeed(Schrodinger)
137.035999084

julia> vacuumpermeability(Schrodinger)
0.0006691762566203905

julia> electronmass(Schrodinger)
4.899602291219254e-22
```
