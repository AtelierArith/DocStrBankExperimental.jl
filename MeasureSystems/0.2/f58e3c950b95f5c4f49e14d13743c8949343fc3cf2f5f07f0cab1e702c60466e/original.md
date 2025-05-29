```Julia
newton(U::UnitSystem) = force(𝟏,U,Metric)
force : [F], [F], [MLT⁻²], [MLT⁻²], [MLT⁻²]
F⋅(𝘩⁻¹𝘤⁻¹R∞⁻²α⁴τ⁻¹2⁻² = 4.7166761794(29)) [ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] Unified
```

Metric `newton` unit of `force` (N or lb).

```Julia
julia> newton(Metric) # N
𝟏 = 1.0 [N] Metric

julia> newton(CGS) # dyn
2⁵5⁵ = 100000.0 [dyn] Gauss

julia> newton(English) # lb
g₀⁻¹lb⁻¹ = 0.22480894309971047 [lbf] English

julia> newton(FPS) # pdl
ft⁻¹lb⁻¹ = 7.233013851209893 [pdl] FPS

julia> newton(Engineering) # kp
g₀⁻¹ = 0.10197162129779283 [kgf] Engineering
```
