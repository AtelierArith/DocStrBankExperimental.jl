```Julia
entropy(U::UnitSystem,S::UnitSystem) = energy(U,S)/temperature(U,S)
entropy(v::Real,U::UnitSystem,S::UnitSystem) = v/entropy(U,S)
```

熱容量または `energy` あたりの `temperature` または `entropy` (J⋅K⁻¹)、単位換算係数。

```Julia
julia> entropy(Metric,SI2019) # K⋅K⁻¹
1.000000000343744

julia> entropy(CGS,Metric) # J⋅erg⁻¹
1.0000000000000001e-7

julia> entropy(English,SI2019) # J⋅°R⋅K⁻¹⋅ft⁻¹⋅lb⁻¹
2.440472307835418

julia> entropy(Survey,English) # ftUS²⋅°R⋅°ft⁻²⋅°R⁻¹
1.000002000004
```
