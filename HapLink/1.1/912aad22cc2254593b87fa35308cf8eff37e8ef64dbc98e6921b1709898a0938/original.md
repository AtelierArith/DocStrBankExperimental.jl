```
variations_match(reference::Pseudoread, query::Union{Pseudoread,Haplotype})
```

Returns `true` if `query` could be a read from `reference`.

Additional `Variation`s found within `query` that are not present in `reference` **do not** invalid a positive match result so long as none of those `Variation`s [`contradicts`](@ref) `reference`. These `Variation`s can either

1. Extend beyond the length of `reference`, or
2. Exist as "sequencing errors" within the interval of `reference`

On the other hand, **every** `Variation` within the overlapping interval of `reference` and `query` that is present in `reference` **must** also be found in `query`. In other words, `query` must have all of `reference` (within the overlap), but `reference` does not need all of `query`.

This arrangment allows for the creation of bodies of matching [`Pseudoread`](@ref)s, as done via [`simulate`](@ref).
