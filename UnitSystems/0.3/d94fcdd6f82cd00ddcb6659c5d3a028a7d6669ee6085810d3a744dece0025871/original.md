```Julia
gforce(U::UnitSystem) = specificforce(𝟏,U,English)
```

Standard gravity `specificforce` `g₀` at geodetic reference latitude (m⋅s⁻² or ft⋅s⁻²).

```Julia
julia> gforce(CGS) # gal
980.6649999999998

julia> gforce(British) # ft⋅s⁻²
32.17404855643044

julia> gforce(English) # lbf⋅lbm⁻¹
1
```
