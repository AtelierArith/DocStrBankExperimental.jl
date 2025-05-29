```Julia
mobility(U::UnitSystem,S::UnitSystem) = length(U,S)*speed(U,S)/electricpotential(U,S)
mobility(v::Real,U::UnitSystem,S::UnitSystem) = v/mobility(U,S)
```

固体物理学における電子の `mobility` (m²⋅V⁻¹⋅s⁻¹, A⋅s⋅kg⁻¹)、単位変換係数。

```Julia
julia> mobility(EMU,Metric) # C⋅g⋅abC⁻¹⋅kg
1.0000000000000002e-12

julia> mobility(EMU,ESU) # statC⋅abC⁻¹
3.33564095198152e-11

julia> mobility(ESU,Metric) # C⋅g⋅statC⁻¹⋅kg
0.029979245800000012

julia> mobility(Metric,SI2019) # C⋅C⁻¹
1.0000000002726048
```
