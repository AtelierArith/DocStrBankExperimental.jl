```Julia
slinchmole(U::UnitSystem) = molaramount(𝟏,U,IPS)
molaramount : [N], [N], [N], [N], [N]
N⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²g₀⋅ft⁻¹lb⋅2⋅3 = 1.92248829321(59) × 10³²) [mₑ⋅Mᵤ⁻¹] Unified
```

Molecular `molaramount` unit (mol or lb-mol).

```Julia
julia> slinchmole(Metric) # mol
g₀⋅ft⁻¹lb⋅2⁵3⋅5³ = 175126.83524647637 [mol] Metric

julia> slinchmole(English) # lb-mol
g₀⋅ft⁻¹2²3 = 386.0885826771653 [lb-mol] English

julia> slinchmole(British) # slug-mol
2²3 = 12.0 [slug-mol] British
```
