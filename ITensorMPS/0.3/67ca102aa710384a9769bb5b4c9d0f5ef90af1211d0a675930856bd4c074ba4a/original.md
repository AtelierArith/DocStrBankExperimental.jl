```
MPS(sites::Vector{<:Index},states)
```

Construct a product state MPS having site indices `sites`, and which corresponds to the initial state given by the array `states`. The `states` array may consist of either an array of integers or strings, as recognized by the `state` function defined for the relevant Index tag type.

# Examples

```julia
N = 10
sites = siteinds("S=1/2", N)
states = [isodd(n) ? "Up" : "Dn" for n in 1:N]
psi = MPS(sites, states)
```
