```
PoissonMixtureModel
```

A Poisson Mixture Model for clustering and density estimation.

## Fields

  * `k::Int`: Number of poisson-distributed clusters.
  * `λₖ::Vector{Float64}`: Means of each cluster.
  * `πₖ::Vector{Float64}`: Mixing coefficients for each cluster.

## Examples

`julia pmm = PoissonMixtureModel(3) # 3 clusters, 2-dimensional data fit!(pmm, data)`
