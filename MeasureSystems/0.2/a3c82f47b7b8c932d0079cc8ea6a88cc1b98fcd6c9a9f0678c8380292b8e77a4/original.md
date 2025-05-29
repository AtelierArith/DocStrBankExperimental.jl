```Julia
QCDGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,𝟏/μₚₑ)
F=M², M=M, L=M⁻¹, T=M⁻¹, Q=Q, Θ=M, N=M, J=M², A=𝟙, R=𝟙, C=𝟙
```

Qunatum chromodynamics (Gauss) `UnitSystem` based on the `protonmass` scale.

```Julia
julia> boltzmann(QCDGauss)
𝟏 = 1.0 [𝟙] QCDGauss

julia> planckreduced(QCDGauss)
𝟏 = 1.0 [𝟙] QCDGauss

julia> lightspeed(QCDGauss)
𝟏 = 1.0 [𝟙] QCDGauss

julia> vacuumpermeability(QCDGauss)
τ⋅2 = 12.566370614359172 [𝘦ₙ⁻²] QCDGauss

julia> electronmass(QCDGauss)
μₑᵤ⋅μₚᵤ⁻¹ = 0.000544617021487(33) [mₚ] QCDGauss
```

The well known `QCDGauss` values for `length`, `time`, `mass`, and `charge` are:

```Julia
julia> length(QCDGauss,SI2019) # lQCD
R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹τ⁻¹2⁻¹ = 2.10308910335(66) × 10⁻¹⁶ [m]/[mₚ⁻¹] QCDGauss -> SI2019

julia> time(QCDGauss,SI2019) # tQCD
𝘤⁻¹R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹τ⁻¹2⁻¹ = 7.0151501388(22) × 10⁻²⁵ [s]/[mₚ⁻¹] QCDGauss -> SI2019

julia> mass(QCDGauss,SI2019) # mQCD
𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹μₚᵤ⋅2 = 1.67262192369(52) × 10⁻²⁷ [kg]/[mₚ] QCDGauss -> SI2019

julia> charge(QCDGauss,SI2019) # qQCD
𝘦⋅α⁻¹ᐟ² = 1.87554603778(14) × 10⁻¹⁸ [C]/[𝘦ₙ] QCDGauss -> SI2019
```
