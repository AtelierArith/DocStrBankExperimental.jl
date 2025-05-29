```Julia
kilopond(U::UnitSystem) = force(𝟏,U,Engineering)
force : [F], [F], [MLT⁻²], [MLT⁻²], [MLT⁻²]
F⋅(𝘩⁻¹𝘤⁻¹R∞⁻²α⁴g₀⋅τ⁻¹2⁻² = 46.254792454(28)) [ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] Unified
```

Gravitational `kilopond` unit of `force` used in engineering systems (N or lb).

```Julia
julia> kilopond(Metric) # N
g₀ = 9.80665 [N] Metric

julia> kilopond(CGS) # dyn
g₀⋅2⁵5⁵ = 980665.0 [dyn] Gauss

julia> kilopond(English) # lb
lb⁻¹ = 2.2046226218487757 [lbf] English

julia> kilopond(FPS) # pdl
g₀⋅ft⁻¹lb⁻¹ = 70.9316352839675 [pdl] FPS

julia> kilopond(Engineering) # kp
𝟏 = 1.0 [kgf] Engineering
```
