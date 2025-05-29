```Julia
conductancequantum(U::UnitSystem) = 𝟐*elementarycharge(U)^2/planck(U) # 2/klitzing(U)
```

導電量子 `G₀` は、電気伝導度 (S) の量子化された単位です。

```Julia
julia> conductancequantum(SI2019) # S
7.748091729863649e-5

julia> conductancequantum(Metric) # S
7.748091734087984e-5

julia> conductancequantum(Conventional) # S
7.74809186773062e-5

julia> conductancequantum(CODATA) # S
7.74809173100563e-5

julia> conductancequantum(International) # S
7.751927039496357e-5

julia> conductancequantum(InternationalMean) # S
7.751888299037687e-5

julia> conductancequantum(EMU) # abS
7.748091734087985e-14

julia> conductancequantum(ESU) # statS
6.963637571339509e7
```
