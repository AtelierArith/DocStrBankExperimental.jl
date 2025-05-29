```
pairclustering(𝚽::Matrix{Float64}, GP_star::GraphPart)
```

construct the GraphPart object of the primal graph via pair-clustering algorithm.

# Input Arguments

  * `𝚽::Matrix{Float64}`: graph Laplacian eigenvectors 𝚽
  * `GP_star::GraphPart`: GraphPart object of the dual graph

# Output Argument

  * `GP::GraphPart`: GraphPart object of the primal graph via pair-clustering
