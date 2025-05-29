```
search_result = dtwnn(q, y, dist, rad, [normalizer::Type{Nothing}]; kwargs...)
```

Compute the nearest neighbor to `q` in `y`. An optinal normalizer type can be supplied, see, `ZNormalizer, DiagonalZNormalizer, NormNormalizer`.

# Arguments:

  * `q`: query (the short time series)
  * `y`: data ( the long time series)
  * `dist`: distance
  * `rad`: radius
  * `showprogress`: Defaults to true
  * `prune_endpoints = true`: use endpoint heuristic
  * `prune_envelope  = true`: use envelope heuristic
  * `bsf_multiplier  = 1`: If > 1, require lower bound to exceed `bsf_multiplier*best_so_far`.
  * `saveall = false`: compute a dense result (takes longer, no early stopping methods used). If false, then a vector of lower bounds on the distance is stored in `search_result.dists`, if true, all distances are computed and stored.
  * `avoid`: If an integer index (or set of indices) is provided, this index will be avoided in the search. This is useful in case `q` is a part of `y`.
