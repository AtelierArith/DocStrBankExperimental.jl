```Julia
stilb(U::UnitSystem) = luminance(𝟏,U,Gauss)
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
L⁻²JA⁻²⋅(𝘩⁻¹𝘤⁻²Kcd⁻¹R∞⁻⁴α⁸τ⁻³5⁴ = 3.4349076043(42) × 10⁻³²) [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] 統一

`luminance` の歴史的単位 (lx⋅rad⁻²)。

```

Julia julia> stilb(Engineering) # nt 2⁴5⁴ = 10000.0 [nt] 工学

julia> stilb(MetricDegree) # lm⋅m⁻²deg⁻² τ²2⁻²3⁻⁴5² = 3.0461741978670855 [m⁻²lm⋅deg⁻²] メトリック度

julia> stilb(MetricGradian) # lm⋅m⁻²gon⁻² τ²2⁻⁴ = 2.4674011002723395 [m⁻²lm⋅gon⁻²] メトリックグラジアン

julia> stilb(CGS) # sb 𝟏 = 1.0 [ph] ガウス

julia> stilb(English) # fc ft²2⁴5⁴ = 929.0304000000001 [ft⁻²lm⋅rad⁻²] 英語 ```
