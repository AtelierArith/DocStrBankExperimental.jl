```Julia
Hartree = UnitSystem(𝟏,𝟏,𝟏/α,𝟐*τ*α^2,𝟏)
F=L⁻³, M=𝟙, L=L, T=L², Q=Q, Θ=L⁻², N=𝟙, J=L⁻⁴, A=𝟙, R=𝟙, C=𝟙
```

ボーア半径と基本電荷スケールに基づくハートリー原子単位系 `UnitSystem`。

```Julia
julia> boltzmann(Hartree)
𝟏 = 1.0 [𝟙] Hartree

julia> planckreduced(Hartree)
𝟏 = 1.0 [𝟙] Hartree

julia> lightspeed(Hartree)
α⁻¹ = 137.035999084(21) [a₀⁻¹] Hartree

julia> vacuumpermeability(Hartree)
α²τ⋅2 = 0.00066917625662(21) [a₀⋅𝘦⁻²] Hartree

julia> electronmass(Hartree)
𝟏 = 1.0 [𝟙] Hartree
```

よく知られた `Hartree` 原子単位の値は、`length`、`time`、`mass`、および `charge` について次の通りです：

```Julia
julia> length(Hartree,SI2019) # lA
R∞⁻¹α⋅τ⁻¹2⁻¹ = 5.29177210902(81) × 10⁻¹¹ [m]/[a₀] Hartree -> SI2019

julia> time(Hartree,SI2019) # tA
𝘤⁻¹R∞⁻¹τ⁻¹2⁻¹ = 2.4188843265857(46) × 10⁻¹⁷ [s]/[a₀²] Hartree -> SI2019

julia> mass(Hartree,SI2019) # mA
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg]/[𝟙] Hartree -> SI2019

julia> charge(Hartree,SI2019) # qA
𝘦 = 1.602176634×10⁻¹⁹ [C]/[𝘦] Hartree -> SI2019
```
