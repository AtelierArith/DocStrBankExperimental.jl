```
unioninds(A, B; kwargs...)
```

Return a Vector with indices that are the union of the indices of `A` and `B` (the set union, similar to `Base.union`).

Optional keyword arguments:

  * tags::String - a tag name or comma separated list of tag names that the returned indices must all have
  * plev::Int - common prime level that the returned indices must all have
  * inds - Index or collection of indices. Returned indices must come from this set of indices.
