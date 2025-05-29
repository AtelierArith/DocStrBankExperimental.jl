```
rdpg(N::SpeciesInteractionNetwork, r::Integer, threshold::T) where {T <: AbstractFloat}
```

Returns a binary network predicted using a random dot-product graph on the [`tsvd`](@ref) of the network at rank `r`, where interactions with a score above `threshold` are true.

This approach to RDPG has been shown to be highly predictive under strong data sparsity [Poisot2023Network](@cite).

###### References

[DallaRiva2016Exploring](@citet*)

[Poisot2023Network](@citet*)
