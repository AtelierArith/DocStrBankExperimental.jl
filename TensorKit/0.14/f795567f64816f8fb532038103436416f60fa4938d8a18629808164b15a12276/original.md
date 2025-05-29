```
domain(t::AbstractTensorMap{T,S,N₁,N₂}) -> ProductSpace{S,N₂}
domain(t::AbstractTensorMap{T,S,N₁,N₂}, i::Int) -> S
```

Return the domain of a tensor, i.e. the product space of the input spaces. If `i` is specified, return the `i`-th input space. Implementations should provide `domain(t)`.

See also [`codomain`](@ref) and [`space`](@ref).
