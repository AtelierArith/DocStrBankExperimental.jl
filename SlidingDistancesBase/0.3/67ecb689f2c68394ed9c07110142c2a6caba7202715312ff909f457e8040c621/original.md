```
struct BatchSearchResult{T} <: AbstractSearchResult{T}
```

Stores the result after applying a search over a vector of vectors. An instance `bsr` of this type acts as a number in comparisons, and vectors of BatchSearchResult can be sorted based on the `value`. `BatchSearchResult` can also act like an index into vectors. If the indexed vector `v` is of same type as `target`, then a window into `v` is returned. If the vector is of some other eltype, then `v[bsr.batch_ind]` is returned.

See accessor functions [`value`](@ref), [`location`](@ref), [`payload`](@ref), [`target`](@ref), [`targetlength`](@ref)

# Arguments:

  * `target`: Contains what was searched for
  * `value`: Contains the value of what's found (like the distance or cost etc.)
  * `ind`: Index into the searched vector at which the `value` was found.
  * `batch_ind`: Index of outer vector (or file etc.)
  * `payload`: extra information associated with the search.
