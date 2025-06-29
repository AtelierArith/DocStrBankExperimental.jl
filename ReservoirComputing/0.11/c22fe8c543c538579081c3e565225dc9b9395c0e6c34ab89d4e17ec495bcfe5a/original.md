```
chebyshev_mapping([rng], [T], dims...;
    amplitude=one(T), sine_divisor=one(T),
    chebyshev_parameter=one(T), return_sparse=false)
```

Generate a Chebyshev-mapped matrix [^xie2024]. The first row is initialized using a sine function and subsequent rows are iteratively generated via the Chebyshev mapping. The first row is defined as:

$$
    W[1, j] = \text{amplitude} \cdot \sin(j \cdot \pi / (\text{sine_divisor} 
        \cdot \text{n_cols}))
$$

for j = 1, 2, …, n*cols (with n*cols typically equal to K+1, where K is the number of input layer neurons). Subsequent rows are generated by applying the mapping:

$$
    W[i+1, j] = \cos( \text{chebyshev_parameter} \cdot \acos(W[pi, j]))
$$

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`. `res_size` is assumed to be K+1.

# Keyword arguments

  * `amplitude`: Scaling factor used to initialize the first row. This parameter adjusts the amplitude of the sine function. Default value is one.
  * `sine_divisor`: Divisor applied in the sine function's phase. Default value is one.
  * `chebyshev_parameter`: Control parameter for the Chebyshev mapping in subsequent rows. This parameter influences the distribution of the matrix elements. Default is one.
  * `return_sparse`: If `true`, the function returns the matrix as a sparse matrix. Default is `false`.

# Examples

```jldoctest
julia> input_matrix = chebyshev_mapping(10, 3)
10×3 Matrix{Float32}:
 0.866025  0.866025   1.22465f-16
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
 0.866025  0.866025  -4.37114f-8
```

[^xie2024]: Xie, Minzhi, Qianxue Wang, and Simin Yu. "Time Series Prediction of ESN Based on Chebyshev Mapping and Strongly Connected Topology." Neural Processing Letters 56.1 (2024): 30.
