```Julia
magneticfluxquantum(U::UnitSystem) = planck(U)/𝟐/elementarycharge(U)/lorentz(U)
```

磁束量子 `Φ₀` は `𝟏/josephson(U)` (Wb) です。

```Julia
julia> magneticfluxquantum(SI2019) # Wb
2.0678338484619295e-15

julia> magneticfluxquantum(Metric) # Wb
2.067833847898228e-15

julia> magneticfluxquantum(Conventional) # Wb
2.067833627896234e-15

julia> magneticfluxquantum(International) # Wb
2.0671516878412405e-15

julia> magneticfluxquantum(InternationalMean) # Wb
2.067131023350289e-15

julia> magneticfluxquantum(EMU) # Mx
2.0678338478982275e-7

julia> magneticfluxquantum(ESU) # statWb
6.897551264942854e-18
```
