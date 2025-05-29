```
codomain(t::AbstractTensorMap{T,S,N₁,N₂}) -> ProductSpace{S,N₁}
codomain(t::AbstractTensorMap{T,S,N₁,N₂}, i::Int) -> S
```

Return the codomain of a tensor, i.e. the product space of the output spaces. If `i` is specified, return the `i`-th output space. Implementations should provide `codomain(t)`.

See also [`domain`](@ref) and [`space`](@ref).
