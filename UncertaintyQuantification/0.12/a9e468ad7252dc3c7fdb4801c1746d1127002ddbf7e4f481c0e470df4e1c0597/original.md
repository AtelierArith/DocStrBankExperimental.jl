```
EmpiricalDistribution(x::Vector{<:Real}, n::Integer=10000)

Creates an empirical distribution from the data given in `x` using kernel density estimation.
The kernel used is Gaussian and the bandwidth is obtained through the Sheather-Jones method.
The support is inferred from the kde using numerical root finding.
The `cdf` and `quantile` functions are linearly interpolated using `n` data points.
```
