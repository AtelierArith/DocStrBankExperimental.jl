```
eigDAG_Distance(𝚽, Q, numEigs; edge_weights = 1)
```

compute DAG distances between pairwise graph Laplacian eigenvectors.

# Input Arguments

  * `𝚽::Matrix{Float64}`: matrix of graph Laplacian eigenvectors, 𝜙ⱼ₋₁ (j = 1,...,size(𝚽,1)).
  * `Q::Matrix{Float64}`: incidence matrix of the graph.
  * `numEigs::Int64`: number of eigenvectors considered.
  * `edge_weight::Any`: default value is 1, stands for unweighted graph   (i.e., all edge weights equal to 1). For weighted graph, edge_weight is the   weights vector, which stores the affinity weight of each edge.

# Output Argument

  * `dis::Matrix{Float64}`: a numEigs x numEigs distance matrix, dis[i,j] = d_DAG(𝜙ᵢ₋₁, 𝜙ⱼ₋₁).
