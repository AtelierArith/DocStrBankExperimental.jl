```
fit(d::Type{<:AlphaSubGaussian}, x, m; p=1.0)
```

Fit an aSGN(m) model to data via the covariation method.

The covariation method requires an additional parameter `p`. Ideally, 1 < p < α. In most practical impulsive scenarios p=1.0 is sufficient. `m` is the number of lags in the covariance matrix.

The implementation is based on https://github.com/ahmd-mahm/alpha-SGNm/blob/master/param_est/asgnfit.m

Reference: A. Mahmood and M. Chitre, "Generating random variates for stable sub-Gaussian processes with memory", Signal Processing, Volume 131, Pages 271-279, 2017. (https://doi.org/10.1016/j.sigpro.2016.08.016.)
