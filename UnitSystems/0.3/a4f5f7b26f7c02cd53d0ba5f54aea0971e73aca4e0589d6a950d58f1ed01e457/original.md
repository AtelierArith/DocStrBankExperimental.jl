```Julia
NaturalGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,𝟏)
```

Natural (Gauss) `UnitSystem` with the Gaussian `permeability` value of `4π`.

```Julia
julia> boltzmann(NaturalGauss)
1

julia> planckreduced(NaturalGauss)
1

julia> lightspeed(NaturalGauss)
1

julia> vacuumpermeability(NaturalGauss)
12.566370614359172

julia> electronmass(NaturalGauss)
1
```
