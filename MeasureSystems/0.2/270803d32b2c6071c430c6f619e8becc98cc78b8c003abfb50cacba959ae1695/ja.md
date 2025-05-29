```Julia
galileo(U::UnitSystem) = specificforce(𝟏,U,Gauss)
specificforce : [FM⁻¹], [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²]
FM⁻¹⋅(𝘤⁻²R∞⁻¹α²τ⁻¹2⁻³5⁻² = 4.2966013114(13) × 10⁻³²) [ħ⁻¹𝘤³mₑ⋅ϕ⁻¹g₀⁻²] Unified
```

重力測定に使用される `specificforce` のメートル単位 (m⋅s⁻² または ft⋅s⁻²)。

```Julia
julia> galileo(Metric) # m⋅s⁻²
2⁻²5⁻² = 0.010000000000000002 [m⋅s⁻²] Metric

julia> galileo(CGS) # gal
𝟏 = 1.0 [gal] Gauss

julia> galileo(English) # lbf⋅lbm⁻¹
g₀⁻¹2⁻²5⁻² = 0.0010197162129779284 [g₀] English
```
