```
UMAP_(X::AbstractMatrix[, n_components=2]; <kwargs>) -> UMAP_ object
```

Create a model representing the embedding of data `X` into `n_components`-dimensional space.  The returned model has the following fields:

  * `graph`: the graph representing the fuzzy simplicial set of the manifold of `X`.
  * `embedding`: the `n-component`-dimensional embedding of the data `X`.
  * `data`: a reference to the input data `X`.
  * `knns`: a matrix of indices of `X` representing each point's nearest neighbors according to `metric`.         `knns[j, i]` is the index of point i's jth nearest neighbor.
  * `dists`: the respective distances of the above neighbors.          `dists[j, i]` is the distance of point i's jth nearest neighbor.

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
