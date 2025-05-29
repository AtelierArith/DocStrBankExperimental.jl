```Julia
CosmologicalQuantum = AstronomicalSystem(Metric,tcq,lcq,mcq)
```

宇宙量子スケール `UnitSystem` は `darkenergydensity` によって定義されています。

```Julia
julia> boltzmann(CosmologicalQuantum)
1.0

julia> planckreduced(CosmologicalQuantum)
1.0

julia> lightspeed(CosmologicalQuantum)
1.0

julia> vacuumpermeability(CosmologicalQuantum)
12.566370614359172

julia> electronmass(CosmologicalQuantum)
2.273258104382309e8

julia> molarmass(CosmologicalQuantum)
1

julia> luminousefficacy(CosmologicalQuantum)
1
```
