```
fitprior(data, algo, diss = false;
Kmin = 1,
Kmax = Int(floor(size(data)[end] / 2),
verbose = true)
```

Determines the best prior hyperparameters from the data. A notional clustering is obtained using k-means or k-medoids and the elbow method, and the distances are split into within-cluster distances and inter-cluster distances based on the notional clustering. These distances are then used to fit the prior hyperparameters using MLE and empirical Bayes sampling.

# Required Arguments

  * `data::Union{Vector{Vector{Float64}}, Matrix{Float64}}`: can either be a vector of (possibly multi-dimensional) observations, or a matrix with each column an observation, or a square matrix of pairwise dissimilarities.
  * `algo::String`: must be one of `"k-means"` or `"k-medoids"`.

# Optional Arguments

  * `diss::bool`: if true, `data` will be assumed to be a pairwise dissimilarity matrix.
  * `Kmin::Integer`: minimum number of clusters to scan for the elbow method.
  * `Kmax::Integer`: maximum number of clusters to scan for the elbow method. If left unspecified, it is set to half the number of observations.
  * `verbose::Bool`: if false, disables all info messages and progress bars.

# Returns

An object of type [`PriorHyperparamsList`](@ref).
