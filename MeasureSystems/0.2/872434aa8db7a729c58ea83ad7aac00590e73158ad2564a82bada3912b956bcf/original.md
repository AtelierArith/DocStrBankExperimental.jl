```Julia
inchmercury(U::UnitSystem) = pressure(inHg,U,Metric)
pressure : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸inHg⁻¹τ⁻³2⁻⁴ = 2.3818029610(29) × 10⁻²¹) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] Unified
```

Unit of `pressure` exerted by 1 inch of mercury at standard atmospheric conditions.

```Julia
juila> inchmercury(Metric) # Pa
inHg⁻¹ = 3386.3890000000006 [Pa] Metric

julia> inchmercury(English) # lb⋅ft⁻²
g₀⁻¹ft²lb⁻¹inHg⁻¹ = 70.72620474736304 [lbf⋅ft⁻²] English

julia> inchmercury(IPS) # lb⋅in⁻²
g₀⁻¹ft²lb⁻¹inHg⁻¹2⁻⁴3⁻² = 0.49115419963446555 [lb⋅in⁻²] IPS
```
