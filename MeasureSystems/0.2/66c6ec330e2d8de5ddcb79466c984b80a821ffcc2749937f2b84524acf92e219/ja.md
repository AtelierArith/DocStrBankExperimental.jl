```Julia
Planck = UnitSystem(𝟏,𝟏,𝟏,𝟏,√(𝟐*τ*αG))
F=M², M, L=M⁻¹, T=M⁻¹, Q=𝟙, Θ=M, N=M, J=M², A=𝟙, R=𝟙, C=𝟙
```

Planck `UnitSystem` の `electronmass` 値 `√(4π*αG)` を重力結合を使用して。

```Julia
julia> boltzmann(Planck)
𝟏 = 1.0 [𝟙] Planck

julia> planckreduced(Planck)
𝟏 = 1.0 [𝟙] Planck

julia> lightspeed(Planck)
𝟏 = 1.0 [𝟙] Planck

julia> vacuumpermeability(Planck)
𝟏 = 1.0 [𝟙] Planck

julia> electronmass(Planck)
𝘩⋅𝘤⁻¹R∞⋅α⁻²mP⁻¹τ¹ᐟ²2³ᐟ² = 1.483708(16) × 10⁻²² [M] Planck
```
