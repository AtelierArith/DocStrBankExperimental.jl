```
fit(::Type{KnnModel}, index::AbstractSearchIndex, ctx::AbstractContext, labels::CategoricalArray; k=3, weight=KnnUniformWeightKernel())
```

Creates a new `KnnModel` classifier with the examples indexed by `index` and it associated `labels`

# Arguments:

  * `KnnModel`: the type to dispatch the fit request
  * `index`: the search structure see [`SimilaritySearch.jl`](@ref)
  * `labels`: Categorical array of labels

# Keyword arguments

  * `k`: the number of neighbors to be used.
  * `weight`: the neighbor weighting scheme.
