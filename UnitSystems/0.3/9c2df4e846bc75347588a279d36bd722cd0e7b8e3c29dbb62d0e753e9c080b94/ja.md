```Julia
planckmass(U::UnitSystem) = electronmass(U)/sqrt(coupling(U))
```

重力結合定数 `αG` からのプランク質量因子 `mP` (kg またはスラグ)。

```Julia
juila> planckmass(Metric)*lightspeed(Metric)^2/elementarycharge(Metric) # eV⋅𝘤⁻²
1.2208899360004336e28

juila> planckmass(Metric) # kg
2.176434e-8

juila> planckmass(Metric)/dalton(Metric) # Da
1.310679190735522e19

juila> planckmass(Metric)*lightspeed(Metric)^2/elementarycharge(Metric)/sqrt(𝟐^2*τ) # eV⋅𝘤⁻²
2.435323075935861e27

julia> planckmass(PlanckGauss) # mP
1.0
```
