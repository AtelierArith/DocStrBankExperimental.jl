```Julia
maxwell(U::UnitSystem) = magneticflux(𝟏,U,EMU)
```

`magneticflux` (Wb) の電磁単位。

```Julia
julia> maxwell(Metric) # Wb
9.999999999999999e-9

julia> maxwell(EMU) # Mx
1

julia> maxwell(ESU) # statWb
3.33564095198152e-11
```
