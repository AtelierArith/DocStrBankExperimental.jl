```Julia
lumen(U::UnitSystem) = luminousflux(𝟏,U,Metric)
luminousflux : [J], [J], [J], [J], [J]
J⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻²α⁴τ⁻¹2⁻² = 2.3034677403(14) × 10⁻¹¹) [ħ⁻¹𝘤⁴mₑ²Kcd⋅ϕ⁻¹g₀⁻²] 統一

`luminousflux` の一般的な単位 (lm)。

```

Julia julia> lumen(Metric) # lm 𝟏 = 1.0 [cd] メトリック

julia> lumen(CGS) # lm 𝟏 = 1.0 [cd] ガウス

julia> lumen(English) # lm 𝟏 = 1.0 [lm] 英語 ```
