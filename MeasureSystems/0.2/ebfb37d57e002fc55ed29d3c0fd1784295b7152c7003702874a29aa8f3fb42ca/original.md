```Julia
Schrodinger = UnitSystem(𝟏,𝟏,𝟏/α,𝟐*τ*α^2,√(αG/α))
F=MLT⁻², M, L, T, Q, Θ=T⁻¹, N=M, J=T², A=𝟙, R=𝟙, C=𝟙
```

Schrodinger `UnitSystem` with `permeability` of `4π/αinv^2` and `electronmass` of `√(αG*αinv)`.

```Julia
julia> boltzmann(Schrodinger)
𝟏 = 1.0 [ML²T⁻¹] Schrodinger

julia> planckreduced(Schrodinger)
𝟏 = 1.0 [ML²T⁻¹] Schrodinger

julia> lightspeed(Schrodinger)
α⁻¹ = 137.035999084(21) [LT⁻¹] Schrodinger

julia> vacuumpermeability(Schrodinger)
α²τ⋅2 = 0.00066917625662(21) [MLQ⁻²] Schrodinger

julia> electronmass(Schrodinger)
𝘩⋅𝘤⁻¹R∞⋅α⁻⁵ᐟ²mP⁻¹2 = 4.899602(54) × 10⁻²² [M] Schrodinger
```
