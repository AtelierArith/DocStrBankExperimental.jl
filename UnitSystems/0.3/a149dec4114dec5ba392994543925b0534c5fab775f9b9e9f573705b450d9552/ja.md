```Julia
volumeheatcapacity(U::UnitSystem,S::UnitSystem) = entropy(U,S)/volume(U,S)
volumeheatcapacity(v::Real,U::UnitSystem,S::UnitSystem) = v/volumeheatcapacity(U,S)
```

`エントロピー` あたりの `体積` または `体積熱容量` (J⋅K⁻¹⋅m⁻³)、単位変換係数。

```Julia
julia> volumeheatcapacity(Metric,SI2019) # K⋅K⁻¹
1.000000000343744

julia> volumeheatcapacity(CGS,Metric) # J⋅cm³⋅erg⁻¹⋅m⁻³
0.09999999999999995

julia> volumeheatcapacity(English,SI2019) # J⋅ft²⋅°R⋅K⁻¹⋅lb⁻¹⋅m⁻³
86.18446619422987

julia> volumeheatcapacity(Survey,English) # ftUS⁵°R⋅°ft⁻⁵⋅°R⁻¹
0.9999960000040001
```
