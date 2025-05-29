```Julia
watt(U::UnitSystem) = power(𝟏,U,Metric)
```

Metric `watt` unit of `power` (W or lb⋅ft⋅s⁻¹).

```Julia
julia> watt(Metric) # W
1

julia> watt(English) # lb⋅ft⋅s⁻¹
0.7375621492772654

julia> watt(Engineering) # kgf⋅m⋅s⁻¹
0.10197162129779283
```
