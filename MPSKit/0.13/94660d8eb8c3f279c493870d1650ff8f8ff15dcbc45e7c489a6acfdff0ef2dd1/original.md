```
entanglement_spectrum(ψ, site::Int) -> SectorDict{sectortype(ψ),Vector{<:Real}}
```

Compute the entanglement spectrum at a given site, i.e. the singular values of the gauge matrix to the right of a given site. This is a dictionary mapping the charge to the singular values.

For `InfiniteMPS` and `WindowMPS` the default value for `site` is 0.

For `FiniteMPS` no default value for `site` is given, it is up to the user to specify.
