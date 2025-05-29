```Julia
pressure(U::UnitSystem,S::UnitSystem) = force(U,S)/area(U,S)
pressure(v::Real,U::UnitSystem,S::UnitSystem) = v/pressure(U,S)
```

圧力または応力または `force` を `area` で割ったもの (Pa, N⋅m⁻², kg⋅m⁻¹⋅s⁻²)、単位変換係数。

```Julia
julia> pressure(CGS,Metric) # Pa⋅Ba⁻¹
0.09999999999999996

julia> 1/atm # Pa⋅atm⁻¹
9.869232667160129e-6

julia> pressure(English,Metric) # Pa⋅ft²⋅lb⁻¹
47.88025898033584

julia> pressure(Metric,IPS) # psi⋅Pa⁻¹
0.00014503773773020932
```
