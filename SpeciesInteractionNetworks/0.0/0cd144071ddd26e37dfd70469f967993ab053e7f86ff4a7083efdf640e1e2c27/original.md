```
structuralmodel(::Type{NicheModel}, species::Integer=10, connectance::AbstractFloat=0.2)
```

Generate a food web under the niche model with the given number of species, and an *expected* connectance. Note that by the nature of the niche model algorithm, only the species richness is guaranteed; there is no guarantee that the connectance will be correct.

See [`NicheModel`](@ref) for more information about the niche model.
