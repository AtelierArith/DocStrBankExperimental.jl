```Julia
lambert(U::UnitSystem) = luminance(𝟐/turn(U),U,Gauss)
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻⁴2⋅5⁴ = 1.0933650486(13) × 10⁻³²) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] Unified
```

Historic unit of `luminance` (nt).

```Julia
julia> lambert(Engineering) # nt
τ⁻¹2⁵5⁴ = 3183.098861837907 [nt] Engineering

julia> lambert(MetricDegree) # lm⋅m⁻²deg⁻²
τ⋅2⁻¹3⁻⁴5² = 0.9696273622190719 [m⁻²lm⋅deg⁻²] MetricDegree

julia> lambert(MetricGradian) # lm⋅m⁻²gon⁻²
τ⋅2⁻³ = 0.7853981633974483 [m⁻²lm⋅gon⁻²] MetricGradian

julia> lambert(CGS) # sb
τ⁻¹2 = 0.3183098861837907 [ph] Gauss

julia> lambert(English) # fc
ft²τ⁻¹2⁵5⁴ = 295.71956088528157 [ft⁻²lm⋅rad⁻²] English
```
