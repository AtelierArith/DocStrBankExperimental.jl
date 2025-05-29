```Julia
reyn(U::UnitSystem) = viscosity(𝟏,U,IPS)
```

IPS単位の`viscosity`はレイノルズにちなんで名付けられています (kg⋅m⁻¹⋅s⁻¹ または lb⋅s⋅ft⁻²)。

```Julia
julia> reyn(Metric) # kg⋅m⁻¹⋅s⁻¹
6894.757293168358

julia> reyn(CGS) # g⋅cm⁻¹⋅s⁻¹
68947.57293168356

julia> reyn(English) # lb⋅s⋅ft⁻²
144.0
```
