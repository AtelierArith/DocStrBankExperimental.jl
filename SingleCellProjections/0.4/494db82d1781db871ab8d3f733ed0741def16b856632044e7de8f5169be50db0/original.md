```
svd(data::DataMatrix; nsv=3, var=:copy, obs=:copy, kwargs...)
```

Compute the Singular Value Decomposition (SVD) of `data` using the Random Subspace SVD algorithm from [Halko et al. "Finding structure with randomness: Probabilistic algorithms for constructing approximate matrix decompositions"]. SVD is often used to perform Principal Component Analysis (PCA), which assumes that the data is centered.

  * `nsv` - The number of singular values.
  * `var` - Can be `:copy` (make a copy of source `var`) or `:keep` (share the source `var` object).
  * `obs` - Can be `:copy` (make a copy of source `obs`) or `:keep` (share the source `obs` object).

Additional kwargs related to numerical precision are passed to `SingleCellProjections.implicitsvd`.

See also: [`SingleCellProjections.implicitsvd`](@ref)
