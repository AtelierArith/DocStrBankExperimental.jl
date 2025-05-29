```Julia
hertz(U::UnitSystem) = 𝟏/second(U)
```

周波数のメトリック単位 (s⁻¹)。

```Julia
julia> hertz(Engineering) # rad⋅s⁻¹
1.0

julia> hertz(IAU) # D⁻¹
86400.0
```
