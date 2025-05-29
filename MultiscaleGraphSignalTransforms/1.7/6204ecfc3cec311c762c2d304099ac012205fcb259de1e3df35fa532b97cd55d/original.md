```
vm_ngwp(𝚽::Matrix{Float64}, GP_star::GraphPart)
```

construct varimax NGWP and GP_star.tag in place.

# Input Arguments

  * `𝚽::Matrix{Float64}`: graph Laplacian eigenvectors 𝚽
  * `GP_star::GraphPart`: GraphPart object of the dual graph

# Output Argument

  * `wavelet_packet::Array{Float64,3}`: the varimax NGWP. The first index is for   selecting wavelets at a fixed level; the second index is for selecting the   level `j`; the third index is for selecting elements in the wavelet vector.
