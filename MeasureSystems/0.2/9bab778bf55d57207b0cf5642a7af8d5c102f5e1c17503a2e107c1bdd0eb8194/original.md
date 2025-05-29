```Julia
poundforce(U::UnitSystem) = force(𝟏,U,English)
force : [F], [F], [MLT⁻²], [MLT⁻²], [MLT⁻²]
F⋅(𝘩⁻¹𝘤⁻¹R∞⁻²α⁴g₀⋅lb⋅τ⁻¹2⁻² = 20.9808209330(13)) [ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] Unified
```

English `poundforce` unit of `force` used in engineering systems (N or lb).

```Julia
julia> poundforce(Metric) # N
g₀⋅lb = 4.4482216152605 [N] Metric

julia> poundforce(CGS) # dyn
g₀⋅lb⋅2⁵5⁵ = 444822.16152604995 [dyn] Gauss

julia> poundforce(English) # lb
𝟏 = 1.0 [lbf] English

julia> poundforce(FPS) # pdl
g₀⋅ft⁻¹ = 32.17404855643044 [pdl] FPS

julia> poundforce(Engineering) # kp
lb = 0.45359237 [kgf] Engineering
```
