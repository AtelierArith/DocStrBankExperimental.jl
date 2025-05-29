```
rand_sparse([rng], [T], dims...;
    radius=1.0, sparsity=0.1, std=1.0, return_sparse=false)
```

Create and return a random sparse reservoir matrix. The matrix will be of size specified by `dims`, with specified `sparsity` and scaled spectral radius according to `radius`.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `radius`: The desired spectral radius of the reservoir. Defaults to 1.0.
  * `sparsity`: The sparsity level of the reservoir matrix, controlling the fraction of zero elements. Defaults to 0.1.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.

# Examples

```jldoctest
julia> res_matrix = rand_sparse(5, 5; sparsity=0.5)
5×5 Matrix{Float32}:
 0.0        0.0        0.0        0.0      0.0
 0.0        0.794565   0.0        0.26164  0.0
 0.0        0.0       -0.931294   0.0      0.553706
 0.723235  -0.524727   0.0        0.0      0.0
 1.23723    0.0        0.181824  -1.5478   0.465328
```
