```
scparams([T], X::AbstractSparseMatrix, features;
         method=:poisson,
         min_cells::Integer=5,
         feature_type,
         feature_mask,
         feature_names,
         use_cache=true,
         cache_read=use_cache,
         cache_write=use_cache,
         verbose=true,
         chunk_size=100,
         nthreads=Threads.nthreads(),
         channel_size=nthreads*4)
```

Compute SCTransform parameter estimates from the count matrix `X`, with features as rows and cells as columns. `features` should be a table (e.g. DataFrame or NamedTuple) with feature annotations. `T` is an optional parameter for the type of the output parameter table. It defaults to the same type as `features`. By default, the results are cached in a scratch space using `Scratch.jl`, to avoid unnecessary recomputations across julia sessions.

General:

  * `method` - Decides the algorithm for parameter inference. Can be either `:poisson` or `:nb` (negative binomial). We recommend `:poisson`, which first makes `poission` estimates and then estimates disperation afterwards.
  * `feature_names` - Vector with name for each feature. Only used for `@warn` messages. Defaults to `name` column in `features`, or `id` column if name doesn't exist.
  * `verbose` - If true, will show progress bar and some other information.

Feature selection:

  * `min_cells` - Only features with nonzero counts in at least `min_cells` cells are included.
  * `feature_type` - Convenience parameter used for `feature_mask` default. Defaults to "Gene Expression" if `features` has a `feature_type` column.
  * `feature_mask` - Vector of booleans deciding which features to use. If set explicitly, the `feature_type` parameter is ignored, otherwise `feature_mask` defaults to only choosing the `feature_type` specified.

Cache:

  * `use_cache` - Enable/disabling caching.
  * `cache_read` - More fine-grained control to enable/disable cache reading only.
  * `cache_write` - More fine-grained control to enable/disable cache writing only.

Threading details:

  * `chunk_size` - The number of features to process in one chunk.
  * `nthreads` - How many threads to use from parameter estimation.
  * `channel_size` - How many chunks to keep in the queue.

# Examples

Compute SCTransform parameter estimates (Gene Expression features):

```
julia> scparams(X, features)
```

Compute SCTransform parameter estimates (Antibody Capture features):

```
julia> scparams(X, features; feature_type="Antibody Capture")
```

See also: [`sctransform`](@ref)
