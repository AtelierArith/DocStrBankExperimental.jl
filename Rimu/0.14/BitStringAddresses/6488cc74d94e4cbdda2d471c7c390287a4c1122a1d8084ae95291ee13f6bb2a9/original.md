```
SortedParticleList{N,M,T<:Unsigned}
```

Type for storing sparse fock states. Stores the mode number of each particle as an entry with only its mode stored. The entries are always kept sorted.

Iterating over `SortedParticleList`s yields occupied modes as a tuple of occupation number, mode number, and position in list.

# Constructors

  * `SortedParticleList{N,M,T}(::SVector{N,T})`: unsafe constructor. Does not sort input.
  * `SortedParticleList(arr::AbstractVector)`: convert ONR to `SortedParticleList`
