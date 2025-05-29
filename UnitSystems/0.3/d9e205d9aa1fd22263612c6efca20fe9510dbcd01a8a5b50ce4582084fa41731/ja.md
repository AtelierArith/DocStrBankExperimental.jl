```Julia
magneticpotential(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)*reluctance(U,S)
magneticpotential(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticpotential(U,S)
```

磁気動力（または `magneticpotential`）（A, Gb）、単位換算係数。

```Julia
julia> magneticpotential(EMU,Metric) # A⋅Gb⁻¹
0.7957747154594768

julia> magneticpotential(Metric,SI2019) # A⋅A⁻¹
0.9999999997273952
```
