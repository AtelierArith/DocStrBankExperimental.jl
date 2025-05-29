```Julia
dyne(U::UnitSystem) = force(𝟏,U,Gauss)
force : [F], [F], [MLT⁻²], [MLT⁻²], [MLT⁻²]
F⋅(𝘩⁻¹𝘤⁻¹R∞⁻²α⁴τ⁻¹2⁻⁷5⁻⁵ = 4.7166761794(29) × 10⁻⁵) [ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] 統一

歴史的な `dyne` 単位の `force` (N または lb)。

```

Julia julia> dyne(Metric) # N 2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [N] メトリック

julia> dyne(CGS) # dyn 𝟏 = 1.0 [dyn] ガウス

julia> dyne(English) # lb g₀⁻¹lb⁻¹2⁻⁵5⁻⁵ = 2.248089430997105×10⁻⁶ [lbf] 英語

julia> dyne(FPS) # pdl ft⁻¹lb⁻¹2⁻⁵5⁻⁵ = 7.233013851209893×10⁻⁵ [pdl] FPS

julia> dyne(Engineering) # kp g₀⁻¹2⁻⁵5⁻⁵ = 1.0197162129779284×10⁻⁶ [kgf] エンジニアリング ```
