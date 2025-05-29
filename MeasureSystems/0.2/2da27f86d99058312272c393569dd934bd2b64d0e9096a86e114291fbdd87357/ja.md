```Julia
PlanckGauss = UnitSystem(𝟏,𝟏,𝟏,𝟐*τ,√αG)
F=M², M=M, L=M⁻¹, T=M⁻¹, Q=Q, Θ=M, N=M, J=M², A=𝟙, R=𝟙, C=𝟙
```

プランク（ガウス） `UnitSystem` の `permeability` は `4π` で、電子質量の結合は `√αG` です。

```Julia
julia> boltzmann(PlanckGauss)
𝟏 = 1.0 [𝟙] PlanckGauss

julia> planckreduced(PlanckGauss)
𝟏 = 1.0 [𝟙] PlanckGauss

julia> lightspeed(PlanckGauss)
𝟏 = 1.0 [𝟙] PlanckGauss

julia> vacuumpermeability(PlanckGauss)
τ⋅2 = 12.566370614359172 [𝘦ₙ⁻²] PlanckGauss

julia> electronmass(PlanckGauss)
𝘩⋅𝘤⁻¹R∞⋅α⁻²mP⁻¹2 = 4.185463(46) × 10⁻²³ [mP] PlanckGauss
```

よく知られている `PlanckGauss` の長さ、時間、質量、温度の値は次の通りです：

```Julia
julia> length(PlanckGauss,SI2019) # ℓP
𝘩⋅𝘤⁻¹mP⁻¹τ⁻¹ = 1.616255(18) × 10⁻³⁵ [m]/[mP⁻¹] PlanckGauss -> SI2019

julia> time(PlanckGauss,SI2019) # tP
𝘩⋅𝘤⁻²mP⁻¹τ⁻¹ = 5.391247(59) × 10⁻⁴⁴ [s]/[mP⁻¹] PlanckGauss -> SI2019

julia> mass(PlanckGauss,SI2019) # mP
mP = 2.176434(24) × 10⁻⁸ [kg]/[mP] PlanckGauss -> SI2019

julia> temperature(PlanckGauss,SI2019) # TP
kB⁻¹𝘤²mP = 1.416784(16) × 10³² [K]/[mP] PlanckGauss -> SI2019
```
