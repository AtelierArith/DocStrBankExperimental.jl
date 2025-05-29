```
silhouettes(assignments::Union{AbstractVector, ClusteringResult}, point_dists::Matrix) -> Vector{Float64}
silhouettes(assignments::Union{AbstractVector, ClusteringResult}, points::Matrix;
            metric::SemiMetric, [batch_size::Integer]) -> Vector{Float64}
```

Compute *silhouette* values for individual points w.r.t. given clustering.

Returns the $n$-length vector of silhouette values for each individual point.

# Arguments

  * `assignments::Union{AbstractVector{Int}, ClusteringResult}`: the vector of point assignments (cluster indices)
  * `points::AbstractMatrix`: if metric is nothing it is an $n×n$ matrix of pairwise distances between the points, otherwise it is an $d×n$ matrix of `d` dimensional clustered data points.
  * `metric::Union{SemiMetric, Nothing}`: an instance of Distances Metric object or nothing, indicating the distance metric used for calculating point distances.
  * `batch_size::Union{Integer, Nothing}`: if integer is given, calculate silhouettes in batches of `batch_size` points each, throws `DimensionMismatch` if batched calculation is not supported by given `metric`.

# References

> Peter J. Rousseeuw (1987). *Silhouettes: a Graphical Aid to the Interpretation and Validation of Cluster Analysis*. Computational and Applied Mathematics. 20: 53–65. Marco Gaido (2023). Distributed Silhouette Algorithm: Evaluating Clustering on Big Data

