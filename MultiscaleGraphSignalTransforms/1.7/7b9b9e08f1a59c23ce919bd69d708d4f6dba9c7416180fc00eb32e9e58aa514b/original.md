```
lp_ngwp(𝚽::Matrix{Float64}, W_dual::SparseMatrixCSC{Float64, Int64},
        GP_dual::GraphPart; ϵ::Float64 = 0.3)
```

construct the lapped NGWP and GP.tag in place.

# Input Arguments

  * `𝚽::Matrix{Float64}`: graph Laplacian eigenvectors
  * `W_dual::SparseMatrixCSC{Float64, Int64}`: weight matrix of the dual graph
  * `GP_dual::GraphPart`: GraphPart object of the dual graph

# Output Argument

  * `wavelet_packet::Array{Float64,3}`: the lapped NGWP dictionary. The first   index is for selecting wavelets at a fixed level; the second index is for   selecting the level `j`; the third index is for selecting elements in the   wavelet vector.
