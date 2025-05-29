```Julia
magneticflux(U::UnitSystem,S::UnitSystem) = energy(U,S)/lorentz(U,S)/current(U,S)
magneticflux(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticflux(U,S)
```

表面 `magneticflux` または `energy` あたり `current` (Wb, J⋅A⁻¹, V⋅s)、単位変換係数。

```Julia
julia> magneticflux(EMU,Metric) # Wb⋅Mx⁻¹
1.0e-8

julia> magneticflux(ESU,Metric) # Wb⋅statWb⁻¹
299.79245800000007

julia> magneticflux(Metric,SI2019) # Wb⋅Wb⁻¹
1.0000000002726048
```
