```Julia
Electronic = UnitSystem(𝟏,𝟏/α,𝟏,𝟐*τ,𝟏)
F=T⁻¹, M=𝟙, L=T, T, Q, Θ=𝟙, N=𝟙, J=T⁻¹, A=𝟙, R=𝟙, C=𝟙
```

Electronic `UnitSystem` with `planckreduced` of `1/α` and `permeability` of `4π`.

```Julia
julia> boltzmann(Electronic)
𝟏 = 1.0 [𝟙] Electronic

julia> planckreduced(Electronic)
α⁻¹ = 137.035999084(21) [T] Electronic

julia> lightspeed(Electronic)
𝟏 = 1.0 [𝟙] Electronic

julia> vacuumpermeability(Electronic)
τ⋅2 = 12.566370614359172 [TQ⁻²] Electronic

julia> electronmass(Electronic)
𝟏 = 1.0 [𝟙] Electronic
```
