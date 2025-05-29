```
KmeansResult{C,D<:Real,WC<:Real} <: ClusteringResult
```

The output of [`kmeans`](@ref) and [`kmeans!`](@ref).

# Type parameters

  * `C<:AbstractMatrix{<:AbstractFloat}`: type of the `centers` matrix
  * `D<:Real`: type of the assignment cost
  * `WC<:Real`: type of the cluster weight
