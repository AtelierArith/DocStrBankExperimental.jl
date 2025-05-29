```Julia
nit(U::UnitSystem) = luminance(𝟏,U,Metric)
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻³2⁻⁴ = 3.4349076043(42) × 10⁻³⁶) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] Unified
```

Metric unit of `luminance` (lx⋅rad⁻²).

```Julia
julia> nit(Engineering) # nt
𝟏 = 1.0 [nt] Engineering

julia> nit(MetricDegree) # lm⋅m⁻²deg⁻²
τ²2⁻⁶3⁻⁴5⁻² = 0.0003046174197867087 [m⁻²lm⋅deg⁻²] MetricDegree

julia> nit(MetricGradian) # lm⋅m⁻²gon⁻²
τ²2⁻⁸5⁻⁴ = 0.00024674011002723397 [m⁻²lm⋅gon⁻²] MetricGradian

julia> nit(CGS) # sb
2⁻⁴5⁻⁴ = 0.0001 [ph] Gauss

julia> nit(English) # fc
ft² = 0.09290304 [ft⁻²lm⋅rad⁻²] English
```
