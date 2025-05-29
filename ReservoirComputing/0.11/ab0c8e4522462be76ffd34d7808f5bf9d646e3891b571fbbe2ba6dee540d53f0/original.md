```
chaotic_init([rng], [T], dims...;
    extra_edge_probability=T(0.1), spectral_radius=one(T),
    return_sparse=false)
```

Construct a chaotic reservoir matrix using a digital chaotic system [^xie2024].

The matrix topology is derived from a strongly connected adjacency matrix based on a digital chaotic system operating at finite precision. If the requested matrix order does not exactly match a valid order the closest valid order is used.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `extra_edge_probability`: Probability of adding extra random edges in the adjacency matrix to enhance connectivity. Default is 0.1.
  * `desired_spectral_radius`: The target spectral radius for the reservoir matrix. Default is one.
  * `return_sparse`: If `true`, the function returns the reservoir matrix as a sparse matrix. Default is `false`.

# Examples

```jldoctest
julia> res_matrix = chaotic_init(8, 8)
┌ Warning: 
│ 
│     Adjusting reservoir matrix order:
│         from 8 (requested) to 4
│     based on computed bit precision = 1. 
│ 
└ @ ReservoirComputing ~/.julia/dev/ReservoirComputing/src/esn/esn_inits.jl:805
4×4 SparseArrays.SparseMatrixCSC{Float32, Int64} with 6 stored entries:
   ⋅        -0.600945   ⋅          ⋅ 
   ⋅          ⋅        0.132667   2.21354
   ⋅        -2.60383    ⋅        -2.90391
 -0.578156    ⋅         ⋅          ⋅
```

[^xie2024]: Xie, Minzhi, Qianxue Wang, and Simin Yu. "Time Series Prediction of ESN Based on Chebyshev Mapping and Strongly Connected Topology." Neural Processing Letters 56.1 (2024): 30.
