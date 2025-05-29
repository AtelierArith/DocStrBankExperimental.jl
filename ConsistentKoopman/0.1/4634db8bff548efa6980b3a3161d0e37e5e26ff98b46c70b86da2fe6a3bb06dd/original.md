```
sparseW_sepband(X::Matrix{Float64}, eps::Float64, m̂::Float64, 
D::Matrix{Float64}, N::Matrix{Integer}; NN::Integer = 0, sym::Bool = true)

computes sparse kernel matrix W with gaussian multiple bandwidth kernel from given ϵ, see 10.1038/s41467-021-26357-x supplement and references therein

Arguments
=================
- X: original data (after embedding), where dim 2 is the embedding space of size N
- eps: epsilon value for gaussian kernel, a strictly positive Float64
- m̂: estimate value of dimension x2
- D: distance matrix, with distance info given by matrix N

Keyword arguments
=================
- NN: nearest neighbors used
- sym: boolean for optional operator symmetrization
```
