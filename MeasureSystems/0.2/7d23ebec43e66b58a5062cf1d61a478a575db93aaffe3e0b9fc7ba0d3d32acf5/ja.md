```Julia
gravity(U::UnitSystem) = # 質量*加速度/力
gravityforce : [F⁻¹MLT⁻²], [𝟙], [𝟙], [𝟙], [𝟙]
F⁻¹MLT⁻² [g₀] 統一

技術工学単位で使用される重力の力の参照 (kg⋅m⋅N⁻¹⋅s⁻²)。

```

Julia julia> gravity(Metric) 𝟏 = 1.0 [𝟙] メトリック

julia> gravity(Engineering) # m⋅kg⋅N⁻¹⋅s⁻² g₀ = 9.80665 [kgf⁻¹kg⋅m⋅s⁻²] エンジニアリング

julia> gravity(English) # ft⋅lbm⋅lbf⁻¹⋅s⁻² g₀⋅ft⁻¹ = 32.17404855643044 [lbf⁻¹lbm⋅ft⋅s⁻²] 英語 ```
