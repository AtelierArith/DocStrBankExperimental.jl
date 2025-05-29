```Julia
stilb(U::UnitSystem) = luminance(𝟏,U,Gauss)
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻³5⁴ = 3.4349076043(42) × 10⁻³²) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] Unified
```

Historic unit of `luminance` (lx⋅rad⁻²).

```Julia
julia> stilb(Engineering) # nt
2⁴5⁴ = 10000.0 [nt] Engineering

julia> stilb(MetricDegree) # lm⋅m⁻²deg⁻²
τ²2⁻²3⁻⁴5² = 3.0461741978670855 [m⁻²lm⋅deg⁻²] MetricDegree

julia> stilb(MetricGradian) # lm⋅m⁻²gon⁻²
τ²2⁻⁴ = 2.4674011002723395 [m⁻²lm⋅gon⁻²] MetricGradian

julia> stilb(CGS) # sb
𝟏 = 1.0 [ph] Gauss

julia> stilb(English) # fc
ft²2⁴5⁴ = 929.0304000000001 [ft⁻²lm⋅rad⁻²] English
```
