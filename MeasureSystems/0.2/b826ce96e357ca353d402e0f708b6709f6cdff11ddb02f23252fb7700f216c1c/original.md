```Julia
phot(U::UnitSystem) = illuminance(𝟏,U,Gauss)
illuminance : [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²J⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻³5⁴ = 3.4349076043(42) × 10⁻³²) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻³g₀⁻⁴] Unified
```

Historic unit of `illuminance` (lx).

```Julia
julia> phot(Metric) # lx
2⁴5⁴ = 10000.0 [lx] Metric

julia> phot(CGS) # ph
𝟏 = 1.0 [ph] Gauss

julia> phot(English) # fc
ft²2⁴5⁴ = 929.0304000000001 [fc] English
```
