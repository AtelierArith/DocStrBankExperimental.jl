```
uniqueind(A, B; kwargs...)
```

Return the first `Index` unique to the set of indices of `A` and not in `B`.

See also [`uniqueinds`](@ref).

Optional keyword arguments:

  * tags::String - a tag name or comma separated list of tag names that the returned indices must all have
  * plev::Int - common prime level that the returned indices must all have
  * inds - Index or collection of indices. Returned indices must come from this set of indices.
