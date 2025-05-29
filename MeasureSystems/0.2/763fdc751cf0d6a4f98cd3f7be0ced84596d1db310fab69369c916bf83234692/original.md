```Julia
apostilb(U::UnitSystem) = luminance(𝟐/turn(U),U,Metric)
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻⁴2⁻³ = 1.0933650486(13) × 10⁻³⁶) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] Unified
```

Metric unit of `luminance` (lx⋅rad⁻²).

```Julia
julia> apostilb(Engineering) # nt
τ⁻¹2 = 0.3183098861837907 [nt] Engineering

julia> apostilb(MetricDegree) # lm⋅m⁻²deg⁻²
τ⋅2⁻⁵3⁻⁴5⁻² = 9.696273622190722×10⁻⁵ [m⁻²lm⋅deg⁻²] MetricDegree

julia> apostilb(MetricGradian) # lm⋅m⁻²gon⁻²
τ⋅2⁻⁷5⁻⁴ = 7.853981633974483×10⁻⁵ [m⁻²lm⋅gon⁻²] MetricGradian

julia> apostilb(CGS) # sb
τ⁻¹2⁻³5⁻⁴ = 3.183098861837907×10⁻⁵ [ph] Gauss

julia> apostilb(English) # fc
ft²τ⁻¹2 = 0.029571956088528157 [ft⁻²lm⋅rad⁻²] English
```
