```
KNNonline!{tp}(knnscores::AbstractArray{tp, 1}, x::AbstractArray{tp, 2}, [Q::AbstractArray{tp, 2},] k::Int, dim::Int = 1)
```

compute k-nearest neighbor (gamma) scores from x and write it to knnscores with dim being the dimension of the observations. If the covariance matrix Q is given, the mahalanobis distance is used instead of the euclidean distance.
