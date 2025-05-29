```Julia
gray(U::UnitSystem) = energy(𝟏,U,Metric)/mass(𝟏,U,Metric)
specificenergy : [FM⁻¹L], [L²T⁻²], [L²T⁻²], [L²T⁻²], [L²T⁻²]
FM⁻¹L⋅(𝘤⁻² = 1.1126500560536183×10⁻¹⁷) [𝘤²g₀⁻¹] Unified
```

放射能のメトリック単位 (Gy または m²⋅s⁻²)。

```Julia
julia> gray(Metric) # Gy
𝟏 = 1.0 [J⋅kg⁻¹] Metric
```
