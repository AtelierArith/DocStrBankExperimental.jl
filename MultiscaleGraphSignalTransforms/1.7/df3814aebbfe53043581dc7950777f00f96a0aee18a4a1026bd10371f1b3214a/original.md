```
dualgraph(dist::Matrix{Float64}; method::Symbol = :inverse, σ::Float64 = 1.0)
```

build the dual graph's weight matrix based on the given non-trivial eigenvector metric.

# Input Arguments

  * `dist::Matrix{Float64}`: eigenvector distance matrix
  * `method::Symbol`: default is by taking inverse of the distance between   eigenvectors. Ways to build the dual graph edge weights. Option: `:inverse`,   `:gaussian`.
  * `σ::Float64`: default is `1.0`. Gaussian variance parameter.

# Output Argument

  * `G_star::GraphSig`: A `GraphSig` object containing the weight matrix of the   dual graph.
