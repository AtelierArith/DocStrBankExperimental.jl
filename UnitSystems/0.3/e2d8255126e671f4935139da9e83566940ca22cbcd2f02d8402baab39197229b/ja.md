```Julia
angularwavenumber(U::UnitSystem,S::UnitSystem) = angle(U,S)/length(U,S)
angularwavenumber(v::Real,U::UnitSystem,S::UnitSystem) = v/angularwavenumber(U,S)
```

空間の単位あたりの出現数 (m⁻¹)、単位変換係数。

```Julia
julia> angularwavenumber(CGS,Metric) # cm⋅m⁻¹
99.99999999999999

julia> angularwavenumber(English,Metric) # ft⋅m⁻¹
3.280839895013123
```
