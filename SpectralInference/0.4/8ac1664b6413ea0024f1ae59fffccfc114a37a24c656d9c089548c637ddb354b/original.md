```
spectraldistances(A::AbstractMatrix; [onrows=true, alpha=1.0, q=0.5])
spectraldistances(usv::SVD; [onrows=true, alpha=1.0, q=0.5])
spectraldistances(vecs::AbstactMatrix, vals::AbstractMatrix, intervals::AbstractVector{<:UnitRange})
```

computes the cumulative spectral residual distance for spectral phylogenetic inference

`(∑_{p ∈ P} ||UₚΣₚ||₂)²`

where $P$ are the spectral partitions found with `getintervals`. 

Args:

  * A, usv: AbstractMatrix or SVD factorization (AbstractMatrix is passed to `svd()` before calculation)
  * onrows: if true will compute spectral distances on the left singular vectors (U matrix), if false will calculate on the right singular vectors or (V matrix)
  * alpha, q: are passed to `getintervals()` see its documentation

Returns:

  * distance matrix
