```Julia
bril(U::UnitSystem) = centi*nano*lambert(U)
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻⁴2⁻¹⁰5⁻⁷ = 1.0933650486(13) × 10⁻⁴³) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] Unified
```

Reference unit of `luminance` (nt).

```Julia
julia> bril(Engineering) # nt
τ⁻¹2⁻⁶5⁻⁷ = 3.183098861837907×10⁻⁸ [nt] Engineering

julia> bril(MetricDegree) # lm⋅m⁻²deg⁻²
τ⋅2⁻¹²3⁻⁴5⁻⁹ = 9.69627362219072×10⁻¹² [m⁻²lm⋅deg⁻²] MetricDegree

julia> bril(MetricGradian) # lm⋅m⁻²gon⁻²
τ⋅2⁻¹⁴5⁻¹¹ = 7.853981633974482×10⁻¹² [m⁻²lm⋅gon⁻²] MetricGradian

julia> bril(CGS) # sb
τ⁻¹2⁻¹⁰5⁻¹¹ = 3.1830988618379067×10⁻¹² [ph] Gauss

julia> bril(English) # fc
ft²τ⁻¹2⁻⁶5⁻⁷ = 2.9571956088528156×10⁻⁹ [ft⁻²lm⋅rad⁻²] English
```
