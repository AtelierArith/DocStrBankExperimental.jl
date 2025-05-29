```Julia
radiantintensity(U::UnitSystem,S::UnitSystem) = power(U,S)/solidangle(U,S)
radiantintensity(v::Real,U::UnitSystem,S::UnitSystem) = v/radiantintensity(U,S)
```

放射強度または `power` あたりの `solidangle` (W⋅sr⁻¹, W⋅rad⁻²)、単位変換係数。

```Julia
julia> radiantintensity(CGS,Metric) # W⋅s⋅erg⁻¹
1.0000000000000001e-7

julia> radiantintensity(English,Metric) # W⋅s⋅ft⁻¹⋅lb⁻¹
1.3558179483314003
```
