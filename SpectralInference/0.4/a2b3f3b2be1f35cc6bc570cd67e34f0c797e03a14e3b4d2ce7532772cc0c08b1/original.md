```
calc_spcorr_mtx(vecs::AbstractMatrix{<:Number}, window)
calc_spcorr_mtx(vecs::AbstractMatrix{<:Number}, vals::AbstractVector{<:Number}, window)
```

Calculates pairwise spectral (pearson) correlations for a set of observations. 

Args:

  * vecs: set of left or right singular vectors with observations/features on rows and spectral components on columns
  * vals: vector of singular values
  * window: set of indices of `vecs` columns to compute correlations across

Returns:

  * correlation matrix where each pixel is the correlation between a pair of observations
