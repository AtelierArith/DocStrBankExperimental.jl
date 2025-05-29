```
fit(::Type{<:UMAP}, index_or_data;
    k=15,
    dist::SemiMetric=L2Distance,
    minbatch=0,
    kwargs...)
```

Wrapper for `fit` that computes `n_nearests` nearest neighbors on `index_or_data` and passes these and `kwargs` to regular `fit`.

# Arguments

  * `index_or_data`: an already constructed index (see `SimilaritySearch`), a matrix, or an abstact database (`SimilaritySearch`)

# Keyword arguments

  * `k=15`: number of neighbors to compute
  * `dist=L2Distance()`: A distance function (see `Distances.jl`)
  * `minbatch=0`: controls how parallel computation is made, zero to use `SimilaritySearch` defaults and -1 to avoid parallel computation; passed to `@batch` macro of `Polyester` package.
