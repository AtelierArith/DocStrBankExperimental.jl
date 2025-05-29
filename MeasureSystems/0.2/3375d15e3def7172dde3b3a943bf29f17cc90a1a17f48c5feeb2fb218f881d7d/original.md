```Julia
lux(U::UnitSystem) = illuminance(𝟏,U,Metric)
illuminance : [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²J⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻³2⁻⁴ = 3.4349076043(42) × 10⁻³⁶) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻³g₀⁻⁴] Unified
```

Metric unit of `illuminance` (lx).

```Julia
julia> lux(Metric) # lx
𝟏 = 1.0 [lx] Metric

julia> lux(CGS) # ph
2⁻⁴5⁻⁴ = 0.0001 [ph] Gauss

julia> lux(English) # fc
ft² = 0.09290304 [fc] English
```
