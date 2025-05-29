```Julia
molaramount : [N], [N], [N], [N], [N]
molaramount(U::UnitSystem,S::UnitSystem) = mass(U,S)*molality(U,S)
molaramount(v::Real,U::UnitSystem,S::UnitSystem) = v/molaramount(U,S)
N [mₑ⋅Mᵤ⁻¹] Unified
```

Amount of molecular substance or `molaramount` (mol), unit conversion factor.

```Julia
julia> molaramount(SI2019,Metric) # mol⋅mol⁻¹
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 0.99999999966(31) [mol]/[mol] SI2019 -> Metric

julia> molaramount(British,SI2019) # mol⋅slug-mol⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅lb⋅2⁻¹ = 453.59237016(14) [mol]/[lb-mol] English -> SI2019

julia> molaramount(English,SI2019) # mol⋅lb-mol⁻¹
NA⁻¹𝘩⁻¹𝘤⋅R∞⁻¹α²μₑᵤ⋅lb⋅2⁻¹ = 453.59237016(14) [mol]/[lb-mol] English -> SI2019
```
