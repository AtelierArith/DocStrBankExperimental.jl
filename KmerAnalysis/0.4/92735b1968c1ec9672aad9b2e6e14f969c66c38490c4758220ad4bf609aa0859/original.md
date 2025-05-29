```
collapse_into_counts(mers::Vector{M}) where {M<:AbstractMer}
```

Build a vector of sorted `MerCount`s from a Vector of a mer type.

This is a basic kernel function used for any higher level and more complex kmer counting procedures.

!!! note
    The input vector `mers` will be sorted by this method.

