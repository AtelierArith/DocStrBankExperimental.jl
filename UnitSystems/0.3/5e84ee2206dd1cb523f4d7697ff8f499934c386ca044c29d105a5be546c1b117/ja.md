```Julia
sealevel(U::UnitSystem) = temperature(T₀+𝟑*𝟓,U)
```

標準の `temperature` 参照は `sealevel` で (K または °R)。

```Julia
julia> sealevel(Metric) # K
288.15

julia> sealevel(SI2019) # K
288.14999990095015

julia> sealevel(English) # °R
518.67
```
