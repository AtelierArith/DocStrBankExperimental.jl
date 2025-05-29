```Julia
NaturalGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,𝟏)
F=𝟙, M=𝟙, L=𝟙, T=𝟙, Q=Q, Θ=𝟙, N=𝟙, J=𝟙, A=𝟙, R=𝟙, C=𝟙
```

Natural (Gauss) `UnitSystem` with the Gaussian `permeability` value of `4π`.

```Julia
julia> boltzmann(NaturalGauss)
𝟏 = 1.0 [𝟙] NaturalGauss

julia> planckreduced(NaturalGauss)
𝟏 = 1.0 [𝟙] NaturalGauss

julia> lightspeed(NaturalGauss)
𝟏 = 1.0 [𝟙] NaturalGauss

julia> vacuumpermeability(NaturalGauss)
τ⋅2 = 12.566370614359172 [𝘦ₙ⁻²] NaturalGauss

julia> electronmass(NaturalGauss)
𝟏 = 1.0 [𝟙] NaturalGauss
```
