```Julia
slugmole(U::UnitSystem) = molaramount(𝟏,U,British)
molaramount : [N], [N], [N], [N], [N]
N⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⋅ft⁻¹lb⋅2⁻¹ = 1.60207357768(49) × 10³¹) [mₑ⋅Mᵤ⁻¹] Unified
```

Molecular `molaramount` unit (mol or lb-mol).

```Julia
julia> slugmole(Metric) # mol
g₀⋅ft⁻¹lb⋅2³5³ = 14593.902937206363 [mol] Metric

julia> slugmole(English) # lb-mol
g₀⋅ft⁻¹ = 32.17404855643044 [lb-mol] English

julia> slugmole(British) # slug-mol
𝟏 = 1.0 [slug-mol] British
```
