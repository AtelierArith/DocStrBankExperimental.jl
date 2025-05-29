```
Variation{S<:BioSequence,T<:BioSymbol}
```

A single change to a biological sequence. A general wrapper that can represent a sequence-specific [`Substitution`](@ref), [`Deletion`](@ref) or [`Insertion`](@ref). `Variation` is more robust than [`Edit`](@ref), due to inclusion of the reference sequence and built-in validation.

# Constructors

```
Variation(ref::S, e::Edit{S,T}) where {S<:BioSequence,T<:BioSymbol}
Variation(ref::S, edit::AbstractString) where {S<:BioSequence}
```

Generally speaking, the `Edit` constructor should be avoided to ensure corectness: use of [`variations(::Haplotype)`](@ref) is encouraged, instead.

Constructing a `Variation` from an `AbstractString` will parse the from `edit` using the following syntax:

  * Substitution: `"<REFBASE><POS><ALTBASE>"`, e.g. `"G16C"`
  * Deletion: `"Δ<STARTPOS>-<ENDPOS>"`, e.g. `"Δ1-2"`
  * Insertion: `"<POS><ALTBASES>"`, e.g. `"11T"`
