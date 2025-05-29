```Julia
massflow : [MT⁻¹], [FL⁻¹T], [MT⁻¹], [MT⁻¹], [MT⁻¹]
massflow(U::UnitSystem,S::UnitSystem) = mass(U,S)/time(U,S)
massflow(v::Real,U::UnitSystem,S::UnitSystem) = v/massflow(U,S)
MT⁻¹ [ħ⁻¹𝘤²mₑ²ϕ⁻¹g₀⁻¹] 統一

```

`massflow` または `mass` の時間あたりのレート (kg⋅s⁻¹)、単位変換係数。

```Julia
julia> massflow(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [kg]/[g] ガウス -> メトリック

julia> massflow(CODATA,Metric) # kg⋅kg⁻¹
𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [kg]/[kg] CODATA -> メトリック

julia> massflow(Conventional,Metric) # kg⋅kg⁻¹
𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [kg]/[kg] 従来 -> メトリック

julia> massflow(English,Metric) # kg⋅slug⁻¹
lb = 0.45359237 [kg]/[lbm] 英語 -> メトリック
```
