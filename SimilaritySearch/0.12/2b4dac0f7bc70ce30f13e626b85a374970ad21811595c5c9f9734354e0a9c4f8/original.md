```
closestpair(idx::AbstractSearchIndex, ctx::AbstractContext; minbatch=0)
```

Finds the closest pair among all elements in `idx`. If the index `idx` is approximate then pair of points could be also an approximation.

# Arguments:

  * `idx`: the search structure that indexes the set of points
  * `ctx`: the search context (caches, hyperparameters, etc)

# Keyword Arguments:

  * `minbatch`: controls how multithreading is used for evaluating configurations, see [`getminbatch`](@ref)
