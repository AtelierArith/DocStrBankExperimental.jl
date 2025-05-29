```
TDE(datacube::Array{tp, 4}, ΔT::Integer, DIM::Int = 3) where {tp}
TDE(datacube::Array{tp, 3}, ΔT::Integer, DIM::Int = 3) where {tp}
```

returns an embedded datacube by concatenating lagged versions of the 2-, 3- or 4-dimensional datacube with `ΔT` time steps in the past up to dimension `DIM` (presetting: `DIM = 3`)

# Examples

```
julia> dc = randn(50,3)
julia> TDE(dc, 3, 2)
```
