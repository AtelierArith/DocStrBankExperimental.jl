```Julia
surveyfoot(U::UnitSystem) = length(𝟏,U,Survey)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ftUS⋅τ⋅2 = 7.8931320544(24) × 10¹¹) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

```

調査単位の `length` (m または ft)。

```Julia
julia> surveyfoot(Metric) # m
ftUS = 0.3048006096012192 [m] メトリック

julia> surveyfoot(English) # ft
ft⁻¹ftUS = 1.0000020000039997 [ft] 英語

julia> surveyfoot(IPS) # in
ft⁻¹ftUS⋅2²3 = 12.000024000047997 [in] IPS
```
