```Julia
QCDoriginal = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ*α,𝟏/μₚₑ)
F=M², M=M, L=M⁻¹, T=M⁻¹, Q=Q, Θ=M, N=M, J=M², A=𝟙, R=𝟙, C=𝟙
```

Qunatum chromodynamics (original) `UnitSystem` scaled by `protonmass` and `elementarycharge`.

```Julia
julia> boltzmann(QCDoriginal)
𝟏 = 1.0 [𝟙] QCDoriginal

julia> planckreduced(QCDoriginal)
𝟏 = 1.0 [𝟙] QCDoriginal

julia> lightspeed(QCDoriginal)
𝟏 = 1.0 [𝟙] QCDoriginal

julia> vacuumpermeability(QCDoriginal)
α⋅τ⋅2 = 0.091701236889(14) [𝘦⁻²] QCDoriginal

julia> electronmass(QCDoriginal)
μₑᵤ⋅μₚᵤ⁻¹ = 0.000544617021487(33) [mₚ] QCDoriginal
```

The well known `QCDoriginal` values for `length`, `time`, `mass`, and `charge` are:

```Julia
julia> length(QCDoriginal,SI2019) # lQCD
R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹τ⁻¹2⁻¹ = 2.10308910335(66) × 10⁻¹⁶ [m]/[mₚ⁻¹] QCDoriginal -> SI2019

julia> time(QCDoriginal,SI2019) # tQCD
𝘤⁻¹R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹τ⁻¹2⁻¹ = 7.0151501388(22) × 10⁻²⁵ [s]/[mₚ⁻¹] QCDoriginal -> SI2019

julia> mass(QCDoriginal,SI2019) # mQCD
𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹μₚᵤ⋅2 = 1.67262192369(52) × 10⁻²⁷ [kg]/[mₚ] QCDoriginal -> SI2019

julia> charge(QCDoriginal,SI2019) # qQCD
𝘦 = 1.602176634×10⁻¹⁹ [C]/[𝘦] QCDoriginal -> SI2019
```
