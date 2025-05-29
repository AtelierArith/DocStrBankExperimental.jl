```
KDEonline!{tp}(kdescores::AbstractArray{tp, 1}, x::AbstractArray{tp, 2} [, Q::AbstractArray{tp, 2}], σ::tp, dim::Int = 1)
```

compute (1.0 - Kernel Density Estimates) from x and write it to kdescores with dim being the dimension of the observations. If teh covariance matrix Q is given, the Mahalanobis distance is used instead of the Euclidean distance.
