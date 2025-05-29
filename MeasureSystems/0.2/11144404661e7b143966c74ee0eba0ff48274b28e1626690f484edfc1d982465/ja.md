```Julia
poundal(U::UnitSystem) = force(𝟏,U,FPS)
force : [F], [F], [MLT⁻²], [MLT⁻²], [MLT⁻²]
F⋅(𝘩⁻¹𝘤⁻¹R∞⁻²α⁴ft⋅lb⋅τ⁻¹2⁻² = 0.65210384999(40)) [ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] 統一

絶対的な英語の `poundal` 単位の `force` (N または lb)。

```

Julia julia> poundal(Metric) # N ft⋅lb = 0.13825495437600002 [N] メトリック

julia> poundal(CGS) # dyn ft⋅lb⋅2⁵5⁵ = 13825.495437600002 [dyn] ガウス

julia> poundal(English) # lb g₀⁻¹ft = 0.031080950171567256 [lbf] 英語

julia> poundal(FPS) # pdl 𝟏 = 1.0 [pdl] FPS

julia> poundal(Engineering) # kp g₀⁻¹ft⋅lb = 0.014098081850173099 [kgf] エンジニアリング ```
