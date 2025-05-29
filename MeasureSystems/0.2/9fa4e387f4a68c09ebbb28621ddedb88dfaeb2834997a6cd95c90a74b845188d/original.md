```Julia
technicalatmosphere(U::UnitSystem) = kilopond(U)/(centi*meter(U))^2
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸g₀⋅τ⁻³5⁴ = 6.8974674816(85) × 10⁻²⁰) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

Gravitational Metric unit of `pressure` (Pa or lb⋅ft⁻²).

```Julia
julia> technicalatmosphere(Metric) # Pa
g₀⋅2⁴5⁴ = 98066.5 [Pa] Metric

julia> technicalatmosphere(English) # lb⋅ft⁻²
ft²lb⁻¹2⁴5⁴ = 2048.161436225217 [lbf⋅ft⁻²] English

julia> technicalatmosphere(IPS) # lb⋅in⁻²
ft²lb⁻¹3⁻²5⁴ = 14.223343307119563 [lb⋅in⁻²] IPS
```
