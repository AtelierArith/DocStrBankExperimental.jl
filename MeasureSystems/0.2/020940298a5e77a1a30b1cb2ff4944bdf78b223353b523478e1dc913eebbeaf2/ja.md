```Julia
barye(U::UnitSystem) = pressure(𝟏,U,Gauss)
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸τ⁻³2⁻⁵5⁻¹ = 7.0334594194(86) × 10⁻²⁶) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] 統一

`pressure` の歴史的単位 (Pa または lb⋅ft⁻²)。

```

Julia julia> barye(Metric) # Pa 2⁻¹5⁻¹ = 0.1 [Pa] メトリック

julia> barye(English) # lb⋅ft⁻² g₀⁻¹ft²lb⁻¹2⁻¹5⁻¹ = 0.002088543423315013 [lbf⋅ft⁻²] 英語

julia> barye(IPS) # lb⋅in⁻² g₀⁻¹ft²lb⁻¹2⁻⁵3⁻²5⁻¹ = 1.4503773773020924×10⁻⁵ [lb⋅in⁻²] IPS ```
