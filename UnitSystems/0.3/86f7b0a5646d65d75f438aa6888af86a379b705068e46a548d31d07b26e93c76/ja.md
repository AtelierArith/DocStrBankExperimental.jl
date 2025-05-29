```Julia
gilbert(U::UnitSystem) = abampere(U)/𝟐/turn(U)
```

磁化の電磁単位 (Gb)。

```Julia
julia> gilbert(Metric) # A⋅rad⁻¹
0.7957747154594768

julia> gilbert(EMU) # Gb
0.07957747154594767

julia> gilbert(ESU) # statA⋅rad⁻¹
2.3856725796184716e9
```
