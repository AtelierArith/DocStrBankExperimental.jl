```
collapse_into_counts!(result::Vector{MerCount{M}}, mers::Vector{M}) where {M<:AbstractMer}
```

Build a vector of sorted `MerCount`s from a Vector of a mer type.

This is a basic kernel function used for any higher level and more complex kmer counting procedures.

This is like `collapse_into_counts`, except it's first argument is a `result` vector that is cleared and filled with the result.

!!! note
    The input vector `mers` will be sorted by this method.

