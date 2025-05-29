```
fit(Type{UMAP}, knns, dists; <kwargs>) -> UMAP object
```

Create a model representing the embedding of data `(X, dist)` into `maxoutdim`-dimensional space. Note that `knns` and `dists` jointly specify the all `k` nearest neighbors of $(X, dist)$, these results must not include self-references. See the `allknn` method in `SimilaritySearch`.

# Arguments

  * `knns`: A $(k, n)$ matrix of integers (identifiers).
  * `dists`: A $(k, n)$ matrix of floating points (distances).

It uses all available threads for the projection.

# Keyword Arguments

  * `maxoutdim::Integer=2`: The number of components in the embedding
  * `n_epochs::Integer = 300`: the number of training epochs for embedding optimization
  * `learning_rate::Real = 1`: the initial learning rate during optimization
  * `learning_rate_decay::Real = 0.9`: how much `learning_rate` is updated on each epoch `(learning_rate *= learning_rate_decay)` (a minimum value is also considered as 1e-6)
  * `layout::AbstractLayout = SpectralLayout()`: how to initialize the output embedding
  * `min_dist::Real = 0.1`: the minimum spacing of points in the output embedding
  * `spread::Real = 1`: the effective scale of embedded points. Determines how clustered embedded points are in combination with `min_dist`.
  * `set_operation_ratio::Real = 1`: interpolates between fuzzy set union and fuzzy set intersection when constructing the UMAP graph (global fuzzy simplicial set). The value of this parameter should be between 1.0 and 0.0: 1.0 indicates pure fuzzy union, while 0.0 indicates pure fuzzy intersection.
  * `local_connectivity::Integer = 1`: the number of nearest neighbors that should be assumed to be locally connected. The higher this value, the more connected the manifold becomes. This should not be set higher than the intrinsic dimension of the manifold.
  * `repulsion_strength::Real = 1`: the weighting of negative samples during the optimization process.
  * `neg_sample_rate::Integer = 5`: the number of negative samples to select for each positive sample. Higher values will increase computational cost but result in slightly more accuracy.
  * `tol::Real = 1e-4`: tolerance to early stopping while optimizing embeddings.
  * `minbatch=0`: controls how parallel computation is made, zero to use `SimilaritySearch` defaults and -1 to avoid parallel computation; passed to `@batch` macro of `Polyester` package.
  * `a = nothing`: this controls the embedding. By default, this is determined automatically by `min_dist` and `spread`.
  * `b = nothing`: this controls the embedding. By default, this is determined automatically by `min_dist` and `spread`.
