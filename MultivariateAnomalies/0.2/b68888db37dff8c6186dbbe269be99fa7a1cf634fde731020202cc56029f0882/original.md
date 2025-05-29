```
dist_matrix(data::AbstractArray{tp, N}; dist::String = "Euclidean", space::Int = 0, lat::Int = 0, lon::Int = 0, Q = 0) where {tp, N}
dist_matrix(data::AbstractArray{tp, N}, training_data; dist::String = "Euclidean", space::Int = 0, lat::Int = 0, lon::Int = 0, Q = 0) where {tp, N}
```

compute the distance matrix of `data` or the distance matrix between data and training data i.e. the pairwise distances along the first dimension of data, using the last dimension as variables. `dist` is a distance metric, currently `Euclidean`(default), `SqEuclidean`, `Chebyshev`, `Cityblock`, `JSDivergence`, `Mahalanobis` and `SqMahalanobis` are supported. The latter two need a covariance matrix `Q` as input argument.

# Examples

```
julia> dc = randn(10, 4,3)
julia> D = dist_matrix(dc, space = 2)
```
