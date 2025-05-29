```
sackurtetrode(U::UnitSystem,P=atm,T=𝟏,m=Da) = log(kB*T/P*sqrt(m*kB*T/τ/ħ^2)^3)+5/2
dimensionless : [𝟙], [𝟙], [𝟙], [𝟙], [𝟙]
log(FL⁻²Θ⁻⁵ᐟ²A³ᐟ²⋅(μₑᵤ⁻³ᐟ²atm⁻¹τ⁻³ᐟ²exp(2⁻¹5) = 0.594141574194(26)))
```

Ideal gas entropy density for pressure `P`, temperature `T`, atomic mass `m` (dimensionless).

```Julia
julia> sackurtetrode(Metric)
log(kB⁵ᐟ²NA⁵ᐟ²𝘩⋅𝘤⁻⁴R∞⁴α⁻⁸μₑᵤ⁻⁴atm⁻¹τ³ᐟ²2²³ᐟ²5¹⁵ᐟ²⋅12.182493960703473) = -1.1648705244 ± 1.2e-9

julia> sackurtetrode(SI2019)
log(kB⁵ᐟ²NA⁵ᐟ²𝘩⋅𝘤⁻⁴R∞⁴α⁻⁸μₑᵤ⁻⁴atm⁻¹τ³ᐟ²2²³ᐟ²5¹⁵ᐟ²⋅12.182493960703473) = -1.1648705244 ± 1.2e-9

julia> sackurtetrode(Conventional)
log(kB⁵ᐟ²NA⁵ᐟ²𝘩⋅𝘤⁻⁴R∞⁴α⁻⁸μₑᵤ⁻⁴atm⁻¹τ³ᐟ²2²³ᐟ²5¹⁵ᐟ²⋅12.182493960703473) = -1.1648705244 ± 1.2e-9

julia> sackurtetrode(CODATA)
log(kB⁵ᐟ²NA⁵ᐟ²𝘩⋅𝘤⁻⁴R∞⁴α⁻⁸μₑᵤ⁻⁴atm⁻¹τ³ᐟ²2²³ᐟ²5¹⁵ᐟ²⋅12.182493960703473) = -1.1648705244 ± 1.2e-9

julia> sackurtetrode(SI2019,𝟏𝟎^5)
log(kB⁵ᐟ²NA⁵ᐟ²𝘩⋅𝘤⁻⁴R∞⁴α⁻⁸μₑᵤ⁻⁴τ³ᐟ²2¹³ᐟ²5⁵ᐟ²⋅12.182493960703473) = -1.1517075379 ± 1.2e-9
```
