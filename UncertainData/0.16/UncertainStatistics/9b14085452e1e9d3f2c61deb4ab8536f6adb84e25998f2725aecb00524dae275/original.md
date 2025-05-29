```
cov(d1::AbstractUncertainValueDataset, d2::AbstractUncertainValueDataset, n::Int; kwargs...)
```

Obtain a distribution for the covariance between two uncertain datasets `d1` and `d2`. This is done by resampling both datasets multiple times and compute the covariance between  those draws. This yields a distribution of covariance estimates. 

The procedure is as follows. 

1. First, draw a realisation of `d1` according to the distributions furnishing its uncertain values.
2. Then, draw a realisation `d2` according to its furnishing distributions.
3. Compute the covariance between those two draws/realisations, both of which are vectors of   length `L = length(d1) = length(d2)`.
4. Repeat the procedure `n` times, drawing `n` separate pairs of realisations of `d1` and `d2`.  This yields `n` estimates of the covariance between `d1` and `d2`, which is returned as   a vector.
