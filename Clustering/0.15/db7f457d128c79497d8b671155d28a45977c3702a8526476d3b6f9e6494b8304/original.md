```
counts(a::ClusteringResult, b::ClusteringResult) -> Matrix{Int}
counts(a::ClusteringResult, b::AbstractVector{<:Integer}) -> Matrix{Int}
counts(a::AbstractVector{<:Integer}, b::ClusteringResult) -> Matrix{Int}
```

Calculate the *cross tabulation* (aka *contingency matrix*) for the two clusterings of the same data points.

Returns the $n_a × n_b$ matrix `C`, where $n_a$ and $n_b$ are the numbers of clusters in `a` and `b`, respectively, and `C[i, j]` is the size of the intersection of `i`-th cluster from `a` and `j`-th cluster from `b`.

The clusterings could be specified either as [`ClusteringResult`](@ref) instances or as vectors of data point assignments.

## See also

[`confusion(a::ClusteringResult, a::ClusteringResult)`](@ref confusion) for 2×2 *confusion matrix*.
