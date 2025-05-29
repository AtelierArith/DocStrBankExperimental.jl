```
median(x::UVAL_COLLECTION_TYPES, n::Int)
```

Obtain a distribution for the median of a collection of uncertain values. This is done by first drawing `n` length-`L` realisations of `x`, where  `L = length(x)`. Then, the median is computed for each of those length-`L` realisations, yielding a distribution of median estimates. 

Detailed steps:

1. First, draw a length-`L` realisation of `x` by drawing one random   number from  each uncertain value furnishing the dataset. The draws are   independent, so that no element-wise dependencies (e.g. sequential  correlations) that are not already present in the data are introduced in   the realisation.
2. Compute the median for the realisation.
3. Repeat the procedure `n` times, drawing `n` independent realisations of `x`.  This yields `n` estimates of the median of `x`, which is returned as   a vector.
