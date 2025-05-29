```
space(t::AbstractTensorMap{T,S,N₁,N₂}) -> HomSpace{S,N₁,N₂}
space(t::AbstractTensorMap{T,S,N₁,N₂}, i::Int) -> S
```

The index information of a tensor, i.e. the `HomSpace` of its domain and codomain. If `i` is specified, return the `i`-th index space.
