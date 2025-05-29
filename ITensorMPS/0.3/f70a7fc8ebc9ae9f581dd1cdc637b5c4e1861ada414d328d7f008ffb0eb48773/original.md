```
ortho_lims(::MPS/MPO)
```

Returns the range of sites of the orthogonality center of the MPS/MPO.

# Examples

```julia
s = siteinds("S=½", 5)
ψ = random_mps(s)
ψ = orthogonalize(ψ, 3)

# ortho_lims(ψ) = 3:3
@show ortho_lims(ψ)

ψ[2] = random_itensor(inds(ψ[2]))

# ortho_lims(ψ) = 2:3
@show ortho_lims(ψ)
```
