```Julia
oersted(U::UnitSystem) = magneticfield(𝟏,U,EMU)
```

電磁単位の `magneticfield` (Oe)。

```Julia
julia> oersted(Metric) # A⋅m⁻¹
79.57747154594766

julia> oersted(EMU) # Oe
1

julia> oersted(ESU) # statA⋅cm⁻¹
2.9979245800000004e10
```
