```
hsp_queries(dist, X::AbstractDatabase, Q::AbstractDatabase, knns, dists; <kwargs>)
hsp_queries(dist, X::AbstractDatabase, Q::AbstractDatabase, k::Integer; <kwargs>)
hsp_queries(idx::AbstractSearchIndex, Q::AbstractDatabase, k::Integer; <kwargs>)
```

Computes the half-space partition of the queries `Q` (possibly given as `knns`, `dists`)

## Optional keyword arguments

  * `ctx::SearchGraphContext` search context (caches)
  * `minbatch::Int`: `Polyester.@batch` parameter controlling how the multithreading is executed
