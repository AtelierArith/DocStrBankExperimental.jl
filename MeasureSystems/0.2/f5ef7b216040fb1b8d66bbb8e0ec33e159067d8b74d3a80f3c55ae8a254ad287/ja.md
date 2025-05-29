```Julia
Rydberg = UnitSystem(𝟏,𝟏,𝟐/α,τ/𝟐*α^2,𝟏/𝟐)
F=MLT⁻², M, L, T, Q, Θ=T⁻¹, N=M, J=T², A=𝟙, R=𝟙, C=𝟙
```

Rydberg `UnitSystem` with `lightspeed` of `𝟐/α` and `permeability` of `π*α^2`.

```Julia
julia> boltzmann(Rydberg)
𝟏 = 1.0 [ML²T⁻¹] Rydberg

julia> planckreduced(Rydberg)
𝟏 = 1.0 [ML²T⁻¹] Rydberg

julia> lightspeed(Rydberg)
α⁻¹2 = 274.071998168(42) [LT⁻¹] Rydberg

julia> vacuumpermeability(Rydberg)
α²τ⋅2⁻¹ = 0.000167294064155(51) [MLQ⁻²] Rydberg

julia> electronmass(Rydberg)
2⁻¹ = 0.5 [M] Rydberg
```

The well known `Rydberg` atomic unit values for `length`, `time`, `mass`, and `charge` are:

```Julia
julia> length(Rydberg,SI2019) # lR
R∞⁻¹α⋅τ⁻¹2⁻¹ = 5.29177210902(81) × 10⁻¹¹ [m]/[a₀] Rydberg -> SI2019

julia> time(Rydberg,SI2019) # tR
𝘤⁻¹R∞⁻¹τ⁻¹ = 4.8377686531713(93) × 10⁻¹⁷ [s]/[T] Rydberg -> SI2019

julia> mass(Rydberg,SI2019) # mR
𝘩⋅𝘤⁻¹R∞⋅α⁻²2² = 1.82187674031(56) × 10⁻³⁰ [kg]/[M] Rydberg -> SI2019

julia> charge(Rydberg,SI2019) # qR
𝘦⋅2⁻¹ᐟ² = 1.1329099625600371×10⁻¹⁹ [C]/[Q] Rydberg -> SI2019
```
