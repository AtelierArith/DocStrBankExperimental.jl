```Julia
faraday(U::UnitSystem) = elementarycharge(U)*avogadro(U)
```

電子のモルあたりの電荷 `𝔉` は、基本電荷に基づいています (C⋅mol⁻¹)。

```Julia
julia> faraday(SI2019) # C⋅mol⁻¹
96485.33212331001

julia> faraday(Metric) # C⋅mol⁻¹
96485.33218277861

julia> faraday(CODATA) # C⋅mol⁻¹
96485.33297110192

julia> faraday(Conventional) # C⋅mol⁻¹
96485.34244809458

julia> faraday(International) # C⋅mol⁻¹
96501.24701069556

julia> faraday(InternationalMean) # C⋅mol⁻¹
96499.8000635266

julia> faraday(EMU) # abC⋅mol⁻¹
9648.533218277862

julia> faraday(ESU) # statC⋅mol⁻¹
2.8925574896021706e14

julia> faraday(Metric)/kilocalorie(Metric) # kcal⋅(V-g-e)⁻¹
23.045470669456353

julia> faraday(Metric)/3600 # A⋅h⋅mol⁻¹
26.801481161882947
```
