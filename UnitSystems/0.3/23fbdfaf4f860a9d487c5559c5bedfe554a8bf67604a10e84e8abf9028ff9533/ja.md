```Julia
PlanckGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,√αG)
```

Planck (Gauss) `UnitSystem` with `permeability` of `4π` and `electronmass` coupling `√αG`.

```Julia
julia> boltzmann(PlanckGauss)
1

julia> planckreduced(PlanckGauss)
1

julia> lightspeed(PlanckGauss)
1

julia> vacuumpermeability(PlanckGauss)
12.566370614359172

julia> electronmass(PlanckGauss)
4.1854628725512725e-23
```

The well known `PlanckGauss` values for `length`, `time`, `mass`, and `temperature` are:

```Julia
julia> length(PlanckGauss,SI2019) # ℓP
1.6162552789315494e-35

julia> time(PlanckGauss,SI2019) # tP
5.391247297260392e-44

julia> mass(PlanckGauss,SI2019) # mP
2.176434e-8

julia> temperature(PlanckGauss,SI2019) # TP
1.416783939059737e32
```
