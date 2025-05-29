```
sackurtetrode(U::UnitSystem,P=atm,T=𝟏,m=Da) = log(kB*T/P*sqrt(m*kB*T/τ/ħ^2)^3)+5/2
dimensionless : [𝟙], [𝟙], [𝟙], [𝟙], [𝟙]
log(FL⁻²Θ⁻⁵ᐟ²A³ᐟ²⋅(μₑᵤ⁻³ᐟ²atm⁻¹τ⁻³ᐟ²exp(2⁻¹5) = 0.594141574194(26)))
```

Ideal gas entropy density for pressure `P`, temperature `T`, atomic mass `m` (dimensionless).

```Julia
julia> sackurtetrode(Metric)
-1.1648705244382895

julia> sackurtetrode(SI2019)
-1.16487052443829

julia> sackurtetrode(Conventional)
-1.1648705244382904

julia> sackurtetrode(CODATA)
-1.16487052443829

julia> sackurtetrode(SI2019,𝟏𝟎^5)
-1.151707537912009
```
