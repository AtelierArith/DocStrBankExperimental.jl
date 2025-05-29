```Julia
poundmole(U::UnitSystem) = molaramount(𝟏,U,English)
molaramount : [N], [N], [N], [N], [N]
N⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²lb⋅2⁻¹ = 4.9793969039(15) × 10²⁹) [mₑ⋅Mᵤ⁻¹] Unified
```

分子の `molaramount` 単位 (mol または lb-mol)。

```Julia
julia> poundmole(Metric) # mol
lb⋅2³5³ = 453.59237 [mol] Metric

julia> poundmole(English) # lb-mol
𝟏 = 1.0 [lb-mol] English

julia> poundmole(British) # slug-mol
g₀⁻¹ft = 0.031080950171567256 [slug-mol] British
```
