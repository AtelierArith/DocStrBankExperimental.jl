```
transform(model::UMAP_, Q::AbstractMatrix; <kwargs>) -> embedding
```

Use the given model to embed new points into an existing embedding. `Q` is a matrix of some number of points (columns) in the same space as `model.data`. The returned embedding is the embedding of these points in n-dimensional space, where n is the dimensionality of `model.embedding`. This embedding is created by finding neighbors of `Q` in `model.embedding` and optimizing cross entropy according to membership strengths according to these neighbors.

# Keyword Arguments

  * `n_neighbors::Integer = 15`: the number of neighbors to consider as locally connected. Larger values capture more global structure in the data, while small values capture more local structure.
  * `metric::{SemiMetric, Symbol} = Euclidean()`: the metric to calculate distance in the input space. It is also possible to pass `metric = :precomputed` to treat `X` like a precomputed distance matrix.
  * `n_epochs::Integer = 300`: the number of training epochs for embedding optimization
  * `learning_rate::Real = 1`: the initial learning rate during optimization
  * `init::Symbol = :spectral`: how to initialize the output embedding; valid options are `:spectral` and `:random`
  * `min_dist::Real = 0.1`: the minimum spacing of points in the output embedding
  * `spread::Real = 1`: the effective scale of embedded points. Determines how clustered embedded points are in combination with `min_dist`.
  * `set_operation_ratio::Real = 1`: interpolates between fuzzy set union and fuzzy set intersection when constructing the UMAP graph (global fuzzy simplicial set). The value of this parameter should be between 1.0 and 0.0: 1.0 indicates pure fuzzy union, while 0.0 indicates pure fuzzy intersection.
  * `local_connectivity::Integer = 1`: the number of nearest neighbors that should be assumed to be locally connected. The higher this value, the more connected the manifold becomes. This should not be set higher than the intrinsic dimension of the manifold.
  * `repulsion_strength::Real = 1`: the weighting of negative samples during the optimization process.
  * `neg_sample_rate::Integer = 5`: the number of negative samples to select for each positive sample. Higher values will increase computational cost but result in slightly more accuracy.
  * `a = nothing`: this controls the embedding. By default, this is determined automatically by `min_dist` and `spread`.
  * `b = nothing`: this controls the embedding. By default, this is determined automatically by `min_dist` and `spread`.
