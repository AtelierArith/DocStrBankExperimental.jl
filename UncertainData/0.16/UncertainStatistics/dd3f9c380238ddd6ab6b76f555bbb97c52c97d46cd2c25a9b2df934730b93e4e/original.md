```
cov(d1::AbstractUncertainValueDataset, d2::AbstractUncertainValueDataset; kwargs...)
```

Obtain a single estimate for the covariance between two uncertain datasets `d1` and `d2`. This is done by resampling both datasets independently, that is: First draw a realisation of  `d1` according to the distributions furnishing its uncertain values. Then, draw a realisation  `d2` according to its furnishing distributions. These those two draws/realisations are now  both vectors of length `L = length(d1) = length(d2)`. Finally, compute the covariance between  those draws. This yields a single estimates of the covariance between `d1` and `d2`.
