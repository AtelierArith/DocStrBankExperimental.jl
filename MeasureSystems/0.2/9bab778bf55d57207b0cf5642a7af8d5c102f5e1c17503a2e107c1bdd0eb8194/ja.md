```Julia
poundforce(U::UnitSystem) = force(𝟏,U,English)
force : [F], [F], [MLT⁻²], [MLT⁻²], [MLT⁻²]
F⋅(𝘩⁻¹𝘤⁻¹R∞⁻²α⁴g₀⋅lb⋅τ⁻¹2⁻² = 20.9808209330(13)) [ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] 統一

English `poundforce` 単位の `force` は工学システムで使用されます (N または lb)。

```

Julia julia> poundforce(Metric) # N g₀⋅lb = 4.4482216152605 [N] メトリック

julia> poundforce(CGS) # dyn g₀⋅lb⋅2⁵5⁵ = 444822.16152604995 [dyn] ガウス

julia> poundforce(English) # lb 𝟏 = 1.0 [lbf] 英語

julia> poundforce(FPS) # pdl g₀⋅ft⁻¹ = 32.17404855643044 [pdl] FPS

julia> poundforce(Engineering) # kp lb = 0.45359237 [kgf] 工学 ```
