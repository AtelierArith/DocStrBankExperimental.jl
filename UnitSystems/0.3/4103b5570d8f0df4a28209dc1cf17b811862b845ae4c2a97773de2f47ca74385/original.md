```Julia
gauss(U::UnitSystem) = magneticfluxdensity(𝟏,U,EMU)
```

Electromagnetic unit of `magneticfluxdensity` (T).

```Julia
julia> gauss(Metric) # T
9.999999999999995e-5

julia> gauss(EMU) # G
1

julia> gauss(ESU) # statT
3.33564095198152e-11
```
