```Julia
mole(U::UnitSystem) = molaramount(𝟏,U,Metric)
molaramount : [N], [N], [N], [N], [N]
N⋅(𝘩⁻¹𝘤⋅R∞⁻¹α²2⁻⁴5⁻³ = 1.09776910575(34) × 10²⁷) [mₑ⋅Mᵤ⁻¹] Unified
```

Molecular `molaramount` unit (mol or lb-mol).

```Julia
julia> mole(Metric) # mol
𝟏 = 1.0 [mol] Metric

julia> mole(English) # lb-mol
lb⁻¹2⁻³5⁻³ = 0.002204622621848776 [lb-mol] English

julia> mole(British) # slug-mol
g₀⁻¹ft⋅lb⁻¹2⁻³5⁻³ = 6.852176585679177×10⁻⁵ [slug-mol] British
```
