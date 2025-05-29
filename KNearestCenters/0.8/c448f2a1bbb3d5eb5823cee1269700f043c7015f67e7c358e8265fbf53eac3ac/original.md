```
fit(::Type{KnnModel}, index::AbstractSearchIndex, meta::AbstractVecOrMat{<:Real}; k=3, weight=KnnUniformWeightKernel(), prediction=KnnSoftmaxPrediction())
fit(::Type{KnnModel}, examples::AbstractMatrix, meta::AbstractVecOrMat{<:Real}; k=3, weight=KnnUniformWeightKernel(), prediction=KnnSoftmaxPrediction(), dist=L2Distance())
```

Creates a new `KnnModel` classifier with the examples indexed by `index` and it associated `labels`

# Arguments:

  * `KnnModel`: the type to dispatch the fit request
  * `index`: the search structure see [`SimilaritySearch.jl`](@ref)
  * `examples`: a matrix that will be indexed using [`SimilaritySearch.jl`](@ref)
  * `meta`: numerical associated data

# Keyword arguments

  * `k`: the number of neighbors to be used.
  * `weight`: the neighbor weighting scheme.
  * `dist`: distance function to be used
