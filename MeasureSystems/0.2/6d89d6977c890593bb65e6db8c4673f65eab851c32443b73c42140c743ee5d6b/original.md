```Julia
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
pressure(U::UnitSystem,S::UnitSystem) = force(U,S)/area(U,S)
pressure(v::Real,U::UnitSystem,S::UnitSystem) = v/pressure(U,S)
FL⁻² [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

Pressure or stress or `force` per `area` (Pa, N⋅m⁻², kg⋅m⁻¹⋅s⁻²), unit conversion factor.

```Julia
julia> pressure(CGS,Metric) # Pa⋅Ba⁻¹
2⁻¹5⁻¹ = 0.1 [Pa]/[Ba] Gauss -> Metric

julia> 1/atm # Pa⋅atm⁻¹
atm⁻¹ = 9.869232667160129×10⁻⁶

julia> pressure(English,Metric) # Pa⋅ft²⋅lb⁻¹
g₀⋅ft⁻²lb = 47.88025898033583 [Pa]/[lbf⋅ft⁻²] English -> Metric

julia> pressure(Metric,IPS) # psi⋅Pa⁻¹
g₀⁻¹ft²lb⁻¹2⁻⁴3⁻² = 0.0001450377377302092 [lb⋅in⁻²]/[Pa] Metric -> IPS
```
