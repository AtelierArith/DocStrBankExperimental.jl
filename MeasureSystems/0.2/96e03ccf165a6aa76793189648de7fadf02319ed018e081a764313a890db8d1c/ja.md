```Julia
gforce(U::UnitSystem) = specificforce(𝟏,U,English)
specificforce : [FM⁻¹], [LT⁻²], [LT⁻²], [LT⁻²], [LT⁻²]
FM⁻¹⋅(𝘤⁻²R∞⁻¹α²g₀⋅τ⁻¹2⁻¹ = 4.2135265250(13) × 10⁻²⁹) [ħ⁻¹𝘤³mₑ⋅ϕ⁻¹g₀⁻²] 統一

標準重力 `specificforce` `g₀` は測地基準緯度で (m⋅s⁻² または ft⋅s⁻²)。

```

Julia julia> gforce(CGS) # gal g₀⋅2²5² = 980.665 [gal] ガウス

julia> gforce(British) # ft⋅s⁻² g₀⋅ft⁻¹ = 32.17404855643044 [ft⋅s⁻²] ブリティッシュ

julia> gforce(English) # lbf⋅lbm⁻¹ 𝟏 = 1.0 [g₀] 英語 ```
