```
cov(x::UVAL_COLLECTION_TYPES, y::UVAL_COLLECTION_TYPES, n::Int; corrected::Bool = true)
```

Obtain a distribution on the covariance between two collections of  uncertain values.

This is done by repeating the following procedure `n` times:

1. First, draw a length-`L` realisation of `x` by drawing one random   number from  each uncertain value furnishing the dataset. The draws are   independent, so that no element-wise dependencies (e.g. sequential  correlations) that are not already present in the data are introduced in   the realisation.
2. Second, draw a length-`L` realisation of `y` in the same manner.
3. Compute the covariance between the two length-`L` draws.

This yields `n` estimates of the covariance between `n` independent pairs  of realisations of `x` and `y`. The `n`-member distribution of covariance  estimates is returned as a vector.

If `corrected` is `true` (the default) then the sum is scaled with `n - 1` for  each pair of draws, whereas the sum is scaled with `n` if `corrected` is `false`  where `n = length(x)`.
