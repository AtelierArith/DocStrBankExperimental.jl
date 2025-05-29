```
MvLocationLowRankScale(location, scale_diag, scale_factors, dist)
```

Variational family with a covariance in the form of a diagonal matrix plus a squared low-rank matrix. The rank is given by `size(scale_factors, 2)`.

It generally represents any distribution for which the sampling path can be represented as follows:

```julia
  d = length(location)
  r = size(scale_factors, 2)
  u_diag = rand(dist, d)
  u_factors = rand(dist, r)
  z = scale_diag.*u_diag + scale_factors*u_factors + location
```
