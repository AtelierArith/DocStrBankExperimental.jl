```
project(y::Vector{TaylorN{T}}, fit::LeastSquaresFit{T}) where {T <: Real}
```

Project the covariance matrix of `fit` into `y`.
