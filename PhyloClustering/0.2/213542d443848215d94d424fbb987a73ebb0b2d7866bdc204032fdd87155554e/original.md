```
gmm_label(tree::AbstractMatrix{<:Real}, n::Int64; method::Symbol=:kmeans, kind::Symbol=:diag)
```

Get predicted labels from Gaussian mixture model for a group of phylogenetic trees.

# Arguments

  * `tree`: a B * N tree Matrix (each column of tree Matrix is a B-dimensional tree in bipartiton format).
  * `n`: the number of clusters.
  * `method`(defaults to `:kmeans`): intialization method to find n starting centers:      * `:kmeans`: use K-means clustering from [Clustering.jl](https://github.com/JuliaStats/Clustering.jl) to initialize with `n` centers.      * `:split`: initialize a single Gaussian with `tree` and subsequently splitting the Gaussians followed by retraining using       the EM algorithm until `n` Gaussians are obtained.
  * `kind`(defaults to `:diag`): covariance type, `:diag` or `:full`.

# Output

A `Tuple{Vector{Int64}, Vector{Int64}}` where the first `Vector` contains predicted labels for each tree based on the posterior probability and     the second `Vector` contain predicted labels for each tree based on the Log Likelihood.
