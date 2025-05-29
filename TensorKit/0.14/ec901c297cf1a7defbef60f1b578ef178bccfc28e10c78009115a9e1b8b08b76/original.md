```
TensorMap(data::AbstractDict{<:Sector,<:AbstractMatrix}, codomain::ProductSpace{S,N₁},
            domain::ProductSpace{S,N₂}) where {S<:ElementarySpace,N₁,N₂}
TensorMap(data, codomain ← domain)
TensorMap(data, domain → codomain)
```

Construct a `TensorMap` by explicitly specifying its block data.

## Arguments

  * `data::AbstractDict{<:Sector,<:AbstractMatrix}`: dictionary containing the block data for each coupled sector `c` as a matrix of size `(blockdim(codomain, c), blockdim(domain, c))`.
  * `codomain::ProductSpace{S,N₁}`: the codomain as a `ProductSpace` of `N₁` spaces of type `S<:ElementarySpace`.
  * `domain::ProductSpace{S,N₂}`: the domain as a `ProductSpace` of `N₂` spaces of type `S<:ElementarySpace`.

Alternatively, the domain and codomain can be specified by passing a [`HomSpace`](@ref) using the syntax `codomain ← domain` or `domain → codomain`.
