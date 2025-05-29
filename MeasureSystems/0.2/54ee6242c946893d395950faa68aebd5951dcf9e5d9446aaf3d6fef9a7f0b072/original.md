```Julia
Natural = UnitSystem(𝟏,𝟏,𝟏,𝟏,𝟏)
F=𝟙, M=𝟙, L=𝟙, T=𝟙, Q=𝟙, Θ=𝟙, N=𝟙, J=𝟙, A=𝟙, R=𝟙, C=𝟙
```

Natural `UnitSystem` with all primary constants having unit value.

```Julia
julia> boltzmann(Natural)
𝟏 = 1.0 [𝟙] Natural

julia> planckreduced(Natural)
𝟏 = 1.0 [𝟙] Natural

julia> lightspeed(Natural)
𝟏 = 1.0 [𝟙] Natural

julia> vacuumpermeability(Natural)
𝟏 = 1.0 [𝟙] Natural

julia> electronmass(Natural)
𝟏 = 1.0 [𝟙] Natural
```

The well known `Natural` values for `length`, `time`, `mass`, and `charge` are:

```Julia
julia> length(Natural,SI2019)
R∞⁻¹α²τ⁻¹2⁻¹ = 3.8615926796(12) × 10⁻¹³ [m]/[𝟙] Natural -> SI2019

julia> time(Natural,SI2019)
𝘤⁻¹R∞⁻¹α²τ⁻¹2⁻¹ = 1.28808866819(39) × 10⁻²¹ [s]/[𝟙] Natural -> SI2019

julia> mass(Natural,SI2019)
𝘩⋅𝘤⁻¹R∞⋅α⁻²2 = 9.1093837016(28) × 10⁻³¹ [kg]/[𝟙] Natural -> SI2019

julia> charge(Natural,SI2019)
𝘦⋅α⁻¹ᐟ²τ⁻¹ᐟ²2⁻¹ᐟ² = 5.29081768990(41) × 10⁻¹⁹ [C]/[𝟙] Natural -> SI2019
```
