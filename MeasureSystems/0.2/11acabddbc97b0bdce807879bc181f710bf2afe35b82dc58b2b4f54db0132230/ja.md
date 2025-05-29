```Julia
CosmologicalQuantum = AstronomicalSystem(Metric,tcq,lcq,mcq)
F=M², M, L=M⁻¹, T=M⁻¹, Q, Θ=M, N=M, J=M², A=𝟙, R=𝟙, C=𝟙
```

宇宙論的量子スケール `UnitSystem` は `darkenergydensity` によって定義されています。

```Julia
julia> boltzmann(CosmologicalQuantum)
𝟏 = 1.0 [𝟙] CosmologicalQuantum

julia> planckreduced(CosmologicalQuantum)
𝟏 = 1.0 [𝟙] CosmologicalQuantum

julia> lightspeed(CosmologicalQuantum)
𝟏 = 1.0 [𝟙] CosmologicalQuantum

julia> vacuumpermeability(CosmologicalQuantum)
τ⋅2 = 12.566370614359172 [𝘦ₙ⁼²] CosmologicalQuantum

julia> electronmass(CosmologicalQuantum)
𝘩¹ᐟ²R∞⋅α⁻²ΩΛ⁻¹ᐟ⁴H0⁻¹ᐟ²au¹ᐟ²mP⁻¹ᐟ²τ¹ᐟ⁴2¹³ᐟ²3⁷ᐟ⁴5³ = 2.2733(84) × 10⁸ [M] CosmologicalQuantum

julia> molarmass(CosmologicalQuantum)
𝟏 = 1.0 [𝟙] CosmologicalQuantum

julia> luminousefficacy(CosmologicalQuantum)
𝟏 = 1.0 [𝟙] CosmologicalQuantum
```
