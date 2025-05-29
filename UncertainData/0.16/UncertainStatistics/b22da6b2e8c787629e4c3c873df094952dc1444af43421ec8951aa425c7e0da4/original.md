```
cor(x::UVAL_COLLECTION_TYPES, y::UVAL_COLLECTION_TYPES, n::Int)
```

Estimate a distribution on Pearson's rank correlation coefficient between  two collections of uncertain values.

This is done by repeating the following procedure `n` times:

1. First, draw a length-`L` realisation of `x` by drawing one random   number from  each uncertain value furnishing the dataset. The draws are   independent, so that no element-wise dependencies (e.g. sequential  correlations) that are not already present in the data are introduced in   the realisation.
2. Second, draw a length-`L` realisation of `y` in the same manner.
3. Compute Pearson's rank correlation coefficient between the two length-`L`  draws.

This yields `n` estimates of Pearson's rank correlation coefficient  between `n` independent pairs of realisations of `x` and `y`. The  `n`-member distribution of correlation estimates is returned as a vector.
