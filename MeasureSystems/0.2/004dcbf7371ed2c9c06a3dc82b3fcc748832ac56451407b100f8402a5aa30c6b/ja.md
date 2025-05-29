```Julia
eotvos(U::UnitSystem) = specificforce(nano,U,Gauss)/length(𝟏,U,Gauss)
nonstandard : [FM⁻¹L⁻¹], [T⁻²], [T⁻²], [T⁻²], [T⁻²]
FM⁻¹L⁻¹⋅(𝘤⁻²R∞⁻²α⁴τ⁻²2⁻¹¹5⁻⁹ = 1.6591724171(10) × 10⁻⁵¹) [ħ⁻²𝘤⁴mₑ²ϕ⁻²g₀⁻³] 統一

重力測定に使用される `specificforce` の `length` のメートル単位 (s⁻² または gal⋅cm⁻¹)。

```

Julia julia> eotvos(Metric) # s⁻² 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [Hz⋅s⁻¹] メトリック

julia> eotvos(CGS) # gal⋅cm⁻¹ 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [gal⋅cm⁻¹] ガウス

julia> eotvos(English) # lbf⋅lbm⁻¹ft⁻¹ g₀⁻¹ft⋅2⁻⁹5⁻⁹ = 3.108095017156726×10⁻¹¹ [lbf⋅lbm⁻¹ft⁻¹] 英語 ```
