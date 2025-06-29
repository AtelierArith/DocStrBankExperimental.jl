```
nullmodel(::Type{C}, N::SpeciesInteractionNetwork{<:Partiteness{T}, <:Binary}, sp::T) where {C <: PermutationConstraint, T}
```

Returns a probabilistic network where the interaction probabilites for species `sp` have been replaced by the probabilities given under the null model specified by the permutation constraint given as its first argument; see [`nullmodel`](@ref). All interactions that do *not* involve species `sp` have their probability set to 1.

The original publication [Saavedra2011Strong](@cite) uses [`Degree`] as the permutation constraint, but this function has been written to be more general.

This network can be passed to [`speciescontribution`](@ref).

###### References

[Saavedra2011Strong](@citet*)
