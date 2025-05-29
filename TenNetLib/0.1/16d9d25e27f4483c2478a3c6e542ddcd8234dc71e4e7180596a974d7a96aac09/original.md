```
function measure(::Type{ElT} = ComplexF64, psi::TTN, opstr::String; kwargs...)
```

Returns (complex / real) local expectation values (`::Vector{ComplexF64}` / `::Vector{Float64}`) of a given TTN `psi::TTN` for a given operator name (`opstr::String`) at all the sites.

Optionally, for specific sites, keyword argument `sites` can be specified, e.g., `sites = [1, 2, 3]`.

For `ElT = Float64`, if the expectation value is complex, raises a warning!
