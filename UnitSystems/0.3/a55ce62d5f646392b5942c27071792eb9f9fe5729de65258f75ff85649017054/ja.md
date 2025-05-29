```Julia
wavenumber(U::UnitSystem,S::UnitSystem) = 1/length(U,S)
wavenumber(v::Real,U::UnitSystem,S::UnitSystem) = v/wavenumber(U,S)
```

空間の単位あたりの出現数 (m⁻¹)、単位変換係数。

```Julia
julia> wavenumber(CGS,Metric) # cm⋅m⁻¹
99.99999999999999

julia> wavenumber(English,Metric) # ft⋅m⁻¹
3.280839895013123
```
