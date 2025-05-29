```Julia
Stoney = UnitSystem(𝟏,𝟏/α,𝟏,𝟐*τ,√(αG/α))
F=MT⁻¹, M, L=T, T, Q, Θ=M, N=M, J, A=𝟙, R=𝟙, C=𝟙
```

Stoney `UnitSystem` の `permeability` は `4π` で、`electronmass` の結合は `√(αG/α)` です。

```Julia
julia> boltzmann(Stoney)
𝟏 = 1.0 [𝟙] Stoney

julia> planckreduced(Stoney)
α⁻¹ = 137.035999084(21) [MT] Stoney

julia> lightspeed(Stoney)
𝟏 = 1.0 [𝟙] Stoney

julia> vacuumpermeability(Stoney)
τ⋅2 = 12.566370614359172 [MTQ⁻²] Stoney

julia> electronmass(Stoney)
𝘩⋅𝘤⁻¹R∞⋅α⁻⁵ᐟ²mP⁻¹2 = 4.899602(54) × 10⁻²² [M] Stoney
```

よく知られた `Stoney` の `length`、`time`、`mass`、および `charge` の値は次のとおりです：

```Julia
julia> length(Stoney,SI2019) # lS
𝘩⋅𝘤⁻¹α¹ᐟ²mP⁻¹τ⁻¹ = 1.380679(15) × 10⁻³⁶ [m]/[T] Stoney -> SI2019

julia> time(Stoney,SI2019) # tS
𝘩⋅𝘤⁻²α¹ᐟ²mP⁻¹τ⁻¹ = 4.605448(51) × 10⁻⁴⁵ [s]/[T] Stoney -> SI2019

julia> mass(Stoney,SI2019) # mS
α¹ᐟ²mP = 1.859209(21) × 10⁻⁹ [kg]/[M] Stoney -> SI2019

julia> charge(Stoney,SI2019) # qS
𝘦 = 1.602176634×10⁻¹⁹ [C]/[𝘦] Stoney -> SI2019
```
