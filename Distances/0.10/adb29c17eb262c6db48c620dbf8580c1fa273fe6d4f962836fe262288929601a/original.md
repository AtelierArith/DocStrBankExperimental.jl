```
SqMahalanobis(Q; skipchecks=false) <: Metric
```

Create a squared Mahalanobis distance (i.e., a bilinear form) with covariance matrix `Q`. Upon construction, both symmetry/self-adjointness and positive semidefiniteness are checked, where the latter check can be skipped by passing the keyword argument `skipchecks = true`.

# Example:

```julia julia> A = collect(reshape(1:9, 3, 3)); Q = A'A;

julia> dist = SqMahalanobis(Q) SqMahalanobis{Matrix{Int64}}([14 32 50; 32 77 122; 50 122 194])

julia> dist = SqMahalanobis(A, skipchecks=true) ┌ Warning: matrix is not symmetric/Hermitian └ @ Distances ... SqMahalanobis{Matrix{Int64}}([1 4 7; 2 5 8; 3 6 9])
