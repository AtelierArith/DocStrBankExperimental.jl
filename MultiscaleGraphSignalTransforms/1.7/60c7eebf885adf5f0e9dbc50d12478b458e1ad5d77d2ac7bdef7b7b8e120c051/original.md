```
getall_expansioncoeffs(G_Sig::GraphSig, GP_star::GraphPart, VM_NGWP::Array{Float64,3}, PC_NGWP::Array{Float64,3}, 𝚽::Matrix{Float64})
```

get all expansion coefficients of `f` via all methods in NGWP.jl and MTSG.jl

# Input Arguments

  * `G_Sig::GraphSig`: GraphSig of the primal graph
  * `GP_star::GraphPart`: GraphPart of the dual graph
  * `VM_NGWP::Array{Float64,3}`: varimax NGWP.
  * `PC_NGWP::Array{Float64,3}`: pair-clustering NGWP.
  * `𝚽::Matrix{Float64}`: the matrix of graph Laplacian eigenvectors.
