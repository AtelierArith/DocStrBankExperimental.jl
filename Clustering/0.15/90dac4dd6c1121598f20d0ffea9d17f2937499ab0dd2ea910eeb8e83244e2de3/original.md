```
wcounts(R::ClusteringResult) -> Vector{Float64}
wcounts(R::FuzzyCMeansResult) -> Vector{Float64}
```

Get the weighted cluster sizes as the sum of weights of points assigned to each cluster.

For non-weighted clusterings assumes the weight of every data point is 1.0, so the result is equivalent to `convert(Vector{Float64}, counts(R))`.
