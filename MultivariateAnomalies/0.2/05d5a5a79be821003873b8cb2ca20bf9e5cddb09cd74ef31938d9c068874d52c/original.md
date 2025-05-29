```
REConline!{tp}(recscores::AbstractArray{tp, 1}, x::AbstractArray{tp, 2} [, Q::AbstractArray{tp, 2}], ɛ::tp, dim::Int = 1)
```

compute recurrence scores from x and write it to recscores with dim being the dimension of the observations. If the covariance matrix Q is given, the mahalanobis distance is used instead of the euclidean distance.
