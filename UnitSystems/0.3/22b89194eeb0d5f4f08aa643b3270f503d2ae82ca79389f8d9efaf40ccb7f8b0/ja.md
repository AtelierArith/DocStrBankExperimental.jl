```Julia
conductivity(U::UnitSystem,S::UnitSystem) = conductance(U,S)/length(U,S)
conductivity(v::Real,U::UnitSystem,S::UnitSystem) = v/conductivity(U,S)
```

逆数の `抵抗率` または電気 `導電率` (S⋅m⁻¹)、単位変換係数。

```Julia
julia> conductivity(EMU,Metric) # S⋅cm⋅abS⁻¹⋅m⁻¹
9.999999999999998e10

julia> conductivity(ESU,Metric) # S⋅cm⋅statS⁻¹⋅m⁼¹
1.1126500560536178e-10

julia> conductivity(Metric,SI2019) # S⋅S⁻¹
0.9999999994547903
```
