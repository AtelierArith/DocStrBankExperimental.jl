```Julia
exposure(U::UnitSystem,S::UnitSystem) = charge(U,S)/mass(U,S)
exposure(v::Real,U::UnitSystem,S::UnitSystem) = v/exposure(U,S)
```

電離放射線の `exposure` または `charge` あたりの `mass` (C⋅kg⁻¹)、単位換算係数。

```Julia
julia> exposure(EMU,Metric) # C⋅g⋅abC⁻¹⋅kg
10000.0

julia> exposure(EMU,ESU) # statC⋅abC⁻¹
2.9979245800000004e10

julia> expsure(ESU,Metric) # C⋅g⋅statC⁻¹⋅kg
3.3356409519815204e-7

julia> exposure(Metric,SI2019) # C⋅C⁻¹
0.9999999997273952
```
