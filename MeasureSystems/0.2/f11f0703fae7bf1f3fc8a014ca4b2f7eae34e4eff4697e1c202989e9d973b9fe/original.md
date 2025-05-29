```Julia
massflow : [MT⁻¹], [FL⁻¹T], [MT⁻¹], [MT⁻¹], [MT⁻¹]
massflow(U::UnitSystem,S::UnitSystem) = mass(U,S)/time(U,S)
massflow(v::Real,U::UnitSystem,S::UnitSystem) = v/massflow(U,S)
MT⁻¹ [ħ⁻¹𝘤²mₑ²ϕ⁻¹g₀⁻¹] Unified
```

Rate of `massflow` or `mass` per `time` (kg⋅s⁻¹), unit conversion factor.

```Julia
julia> massflow(CGS,Metric) # kg⋅g⁻¹
2⁻³5⁻³ = 0.001 [kg]/[g] Gauss -> Metric

julia> massflow(CODATA,Metric) # kg⋅kg⁻¹
𝘩⋅RK⋅KJ²2⁻² = 1.000000017(12) [kg]/[kg] CODATA -> Metric

julia> massflow(Conventional,Metric) # kg⋅kg⁻¹
𝘩⋅RK90⋅KJ90²2⁻² = 1.000000195536555 [kg]/[kg] Conventional -> Metric

julia> massflow(English,Metric) # kg⋅slug⁻¹
lb = 0.45359237 [kg]/[lbm] English -> Metric
```
