```Julia
シュレディンガー = UnitSystem(𝟏,𝟏,𝟏/α,𝟐*τ*α^2,√(αG/α))
F=MLT⁻², M, L, T, Q, Θ=T⁻¹, N=M, J=T², A=𝟙, R=𝟙, C=𝟙
```

シュレディンガー `UnitSystem` の `permeability` は `4π/αinv^2` で、`electronmass` は `√(αG*αinv)` です。

```Julia
julia> boltzmann(シュレディンガー)
𝟏 = 1.0 [ML²T⁻¹] シュレディンガー

julia> planckreduced(シュレディンガー)
𝟏 = 1.0 [ML²T⁻¹] シュレディンガー

julia> lightspeed(シュレディンガー)
α⁻¹ = 137.035999084(21) [LT⁻¹] シュレディンガー

julia> vacuumpermeability(シュレディンガー)
α²τ⋅2 = 0.00066917625662(21) [MLQ⁻²] シュレディンガー

julia> electronmass(シュレディンガー)
𝘩⋅𝘤⁻¹R∞⋅α⁻⁵ᐟ²mP⁻¹2 = 4.899602(54) × 10⁻²² [M] シュレディンガー
```
