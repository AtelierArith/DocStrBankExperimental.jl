```Julia
gforce(U::UnitSystem) = specificforce(𝟏,U,English)
```

標準重力 `specificforce` `g₀` は、測地基準緯度における値です (m⋅s⁻² または ft⋅s⁻²)。

```Julia
julia> gforce(CGS) # gal
980.6649999999998

julia> gforce(British) # ft⋅s⁻²
32.17404855643044

julia> gforce(English) # lbf⋅lbm⁻¹
1
```
