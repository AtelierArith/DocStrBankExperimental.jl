```Julia
candela(U::UnitSystem) = luminousintensity(𝟏,U,Metric)
luminousintensity : [JA⁻²], [J], [J], [J], [J]
JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻²α⁴τ⁻¹2⁻² = 2.3034677403(14) × 10⁻¹¹) [ħ⁻¹𝘤⁴mₑ²Kcd⋅ϕ⁻³g₀⁻²] Unified
```

Common unit of `luminousintensity` (cd).

```Julia
julia> candela(Engineering) # lm⋅rad⁻²
𝟏 = 1.0 [lm⋅rad⁻²] Engineering

julia> candela(MetricDegree) # lm⋅deg⁻²
τ²2⁻⁶3⁻⁴5⁻² = 0.0003046174197867087 [lm⋅deg⁻²] MetricDegree

julia> candela(MetricGradian) # lm⋅gon⁻²
τ²2⁻⁸5⁻⁴ = 0.00024674011002723397 [lm⋅gon⁻²] MetricGradian

julia> candela(CGS) # cd
𝟏 = 1.0 [cd] Gauss

julia> candela(English) # cd
𝟏 = 1.0 [cd] English
```
