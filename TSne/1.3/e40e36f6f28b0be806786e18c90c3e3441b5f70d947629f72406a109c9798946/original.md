```
tsne(X::Union{AbstractMatrix, AbstractVector}, ndims::Integer=2, reduce_dims::Integer=0,
     max_iter::Integer=1000, perplexity::Number=30.0; [keyword arguments])
```

Apply t-SNE (t-Distributed Stochastic Neighbor Embedding) to `X`, i.e. embed its points (rows) into `ndims` dimensions preserving close neighbours.

Returns the points×`ndims` matrix of calculated embedded coordinates.

Different from the orginal implementation, the default is not to use PCA for initialization.

### Arguments

  * `distance` if `true`, specifies that `X` is a distance matrix, if of type `Function` or `Distances.SemiMetric`, specifies the function to use for calculating the distances between the rows (or elements, if `X` is a vector) of `X`
  * `reduce_dims` the number of the first dimensions of `X` PCA to use for t-SNE, if 0, all available dimension are used
  * `pca_init` whether to use the first `ndims` of `X` PCA as the initial t-SNE layout, if `false` (the default), the method is initialized with the random layout
  * `max_iter` how many iterations of t-SNE to do
  * `perplexity` the number of "effective neighbours" of a datapoint, typical values are from 5 to 50, the default is 30
  * `verbose` output informational and diagnostic messages
  * `progress` display progress meter during t-SNE optimization
  * `min_gain`, `eta`, `initial_momentum`, `final_momentum`, `momentum_switch_iter`, `stop_cheat_iter`, `cheat_scale` low-level parameters of t-SNE optimization
  * `extended_output` if `true`, returns a tuple of embedded coordinates matrix, point perplexities and final Kullback-Leibler divergence

See also [Original t-SNE implementation](https://lvdmaaten.github.io/tsne).
