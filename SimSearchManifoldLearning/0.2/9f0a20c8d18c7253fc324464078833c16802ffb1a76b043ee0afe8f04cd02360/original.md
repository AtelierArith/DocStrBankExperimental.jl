```
predict(model::UMAP, Q::AbstractDatabase; k::Integer=15, kwargs...)
predict(model::UMAP, knns, dists; <kwargs>) -> embedding
```

Use the given model to embed new points $Q$ into an existing embedding produced by $(X, dist)$. The second function represent `Q` using its `k` nearest neighbors in `X` under some distance function (`knns` and `dists`) See `searchbatch` in `SimilaritySearch` to compute both (also for `AbstractDatabase` objects).

# Arguments

  * `model`: The fitted model
  * `knns`: matrix of identifiers (integers) of size $(k, |Q|)$
  * `dists`: matrix of distances (floating point values) of size $(k, |Q|)$

Note: the number of neighbors `k` (embedded into knn matrices) control the embedding. Larger values capture more global structure in the data, while small values capture more local structure.

# Keyword Arguments

  * `n_epochs::Integer = 30`: the number of training epochs for embedding optimization
  * `learning_rate::Real = 1`: the initial learning rate during optimization
  * `learning_rate_decay::Real = 0.8`: A decay factor for the `learning_rate` param (on each epoch)
  * `set_operation_ratio::Real = 1`: interpolates between fuzzy set union and fuzzy set intersection when constructing the UMAP graph (global fuzzy simplicial set). The value of this parameter should be between 1.0 and 0.0: 1.0 indicates pure fuzzy union, while 0.0 indicates pure fuzzy intersection.
  * `local_connectivity::Integer = 1`: the number of nearest neighbors that should be assumed to be locally connected. The higher this value, the more connected the manifold becomes. This should not be set higher than the intrinsic dimension of the manifold.
  * `repulsion_strength::Real = 1`: the weighting of negative samples during the optimization process.
  * `neg_sample_rate::Integer = 5`: the number of negative samples to select for each positive sample. Higher values will increase computational cost but result in slightly more accuracy.
  * `tol::Real = 1e-4`: tolerance to early stopping while optimizing embeddings.
  * `minbatch=0`: controls how parallel computation is made. See [`SimilaritySearch.getminbatch`](@ref) and `@batch` (`Polyester` package).
