```
uniqueinds(A, B; kwargs...)
```

Return Vector with indices that are unique to the set of indices of `A` and not in `B` (the set difference, similar to `Base.setdiff`).

Optional keyword arguments:

  * tags::String - a tag name or comma separated list of tag names that the returned indices must all have
  * plev::Int - common prime level that the returned indices must all have
  * inds - Index or collection of indices. Returned indices must come from this set of indices.
