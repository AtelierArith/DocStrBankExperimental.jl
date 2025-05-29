```
repartition(tsrc::AbstractTensorMap{S}, N₁::Int, N₂::Int; copy::Bool=false) where {S}
    -> tdst::AbstractTensorMap{S,N₁,N₂}
```

Return tensor `tdst` obtained by repartitioning the indices of `t`. The codomain and domain of `tdst` correspond to the first `N₁` and last `N₂` spaces of `t`, respectively.

If `copy=false`, `tdst` might share data with `tsrc` whenever possible. Otherwise, a copy is always made.

To repartition into an existing destination, see [repartition!](@ref).
