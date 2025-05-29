```Julia
massflow(U::UnitSystem,S::UnitSystem) = mass(U,S)/time(U,S)
massflow(v::Real,U::UnitSystem,S::UnitSystem) = v/massflow(U,S)
```

`massflow` または `mass` の時間あたりのレート (kg⋅s⁻¹)、単位変換係数。

```Julia
julia> massflow(CGS,Metric) # kg⋅g⁻¹
0.001

julia> massflow(CODATA,Metric) # kg⋅kg⁻¹
1.000000016738611

julia> massflow(Conventional,Metric) # kg⋅kg⁻¹
1.000000195536555

julia> massflow(English,Metric) # kg⋅slug⁻¹
0.45359237
```
