```Julia
QCD = UnitSystem(𝟏,𝟏,𝟏,𝟏,𝟏/μₚₑ)
F=M², M=M, L=M⁻¹, T=M⁻¹, Q=𝟙, Θ=M, N=M, J=M², A=𝟙, R=𝟙, C=𝟙
```

プロトン質量スケールに基づく量子色力学 `UnitSystem`。

```Julia
julia> boltzmann(QCD)
𝟏 = 1.0 [𝟙] QCD

julia> planckreduced(QCD)
𝟏 = 1.0 [𝟙] QCD

julia> lightspeed(QCD)
𝟏 = 1.0 [𝟙] QCD

julia> vacuumpermeability(QCD)
𝟏 = 1.0 [𝟙] QCD

julia> electronmass(QCD)
μₑᵤ⋅μₚᵤ⁻¹ = 0.000544617021487(33) [mₚ] QCD
```

よく知られている `QCD` の `length`、`time`、`mass`、および `charge` の値は次のとおりです。

```Julia
julia> length(QCD,SI2019) # lQCD
R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹τ⁻¹2⁻¹ = 2.10308910335(66) × 10⁻¹⁶ [m]/[mₚ⁻¹] QCD -> SI2019

julia> time(QCD,SI2019) # tQCD
𝘤⁻¹R∞⁻¹α²μₑᵤ⋅μₚᵤ⁻¹τ⁻¹2⁻¹ = 7.0151501388(22) × 10⁻²⁵ [s]/[mₚ⁻¹] QCD -> SI2019

julia> mass(QCD,SI2019) # mQCD
𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹μₚᵤ⋅2 = 1.67262192369(52) × 10⁻²⁷ [kg]/[mₚ] QCD -> SI2019

julia> charge(QCD,SI2019) # qQCD
𝘦⋅α⁻¹ᐟ²τ⁻¹ᐟ²2⁻¹ᐟ² = 5.29081768990(41) × 10⁻¹⁹ [C]/[𝟙] QCD -> SI2019
```
