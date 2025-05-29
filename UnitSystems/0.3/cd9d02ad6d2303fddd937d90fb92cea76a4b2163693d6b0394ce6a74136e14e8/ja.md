```Julia
lineardensity(U::UnitSystem,S::UnitSystem) = mass(U,S)/length(U,S)
lineardensity(v::Real,U::UnitSystem,S::UnitSystem) = v/lineardensity(U,S)
```

`lineardensity` または `mass` の `length` あたりの量 (kg⋅m⁻¹)、単位変換係数。

```Julia
julia> lineardensity(CGS,Metric) # kg⋅cm¹⋅g⁻¹⋅m⁻¹
0.09999999999999998

julia> lineardensity(CGS,British) # slug⋅cm¹⋅g⁻¹⋅ft⁻¹
0.0020885434233150132

julia> lineardensity(English,Metric) # kg⋅ft¹⋅lb⁻¹⋅m⁻¹
1.4881639435695537
```
