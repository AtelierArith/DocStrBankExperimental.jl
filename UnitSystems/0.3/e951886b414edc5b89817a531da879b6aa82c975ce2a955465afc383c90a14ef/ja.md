```Julia
specificvolume(U::UnitSystem,S::UnitSystem) = volume(U,S)/mass(U,S)
specificvolume(v::Real,U::UnitSystem,S::UnitSystem) = v/specificvolume(U,S)
```

密度または質量あたりの体積または比体積の逆数 (m³⋅kg)、単位変換係数。

```Julia
julia> specificvolume(CGS,Metric) # g⋅m³⋅kg⁻¹⋅cm⁻³
0.0010000000000000007

julia> specificvolume(CGS,British) # kg⋅ft³⋅slug⁻¹⋅cm⁻³
0.5153788183931961

julia> specificvolume(English,Metric) # lb⋅m³⋅kg⁻¹⋅ft⁻³
0.062427960576144616
```
