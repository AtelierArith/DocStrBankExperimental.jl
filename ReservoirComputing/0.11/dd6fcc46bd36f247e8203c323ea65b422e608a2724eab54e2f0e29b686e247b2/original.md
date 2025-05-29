```
weighted_init([rng], [T], dims...;
    scaling=0.1, return_sparse=false)
```

Create and return a matrix representing a weighted input layer. This initializer generates a weighted input matrix with random non-zero elements distributed uniformly within the range [-`scaling`, `scaling`] [^lu2017].

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`.

# Keyword arguments

  * `scaling`: The scaling factor for the weight distribution. Defaults to `0.1`.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.

# Examples

```jldoctest
julia> res_input = weighted_init(8, 3)
6×3 Matrix{Float32}:
  0.0452399   0.0          0.0
 -0.0348047   0.0          0.0
  0.0        -0.0386004    0.0
  0.0         0.00981022   0.0
  0.0         0.0          0.0577838
  0.0         0.0         -0.0562827
```

[^lu2017]: Lu, Zhixin, et al. "Reservoir observers: Model-free inference of unmeasured variables in chaotic systems." Chaos: An Interdisciplinary Journal of Nonlinear Science 27.4 (2017): 041102.
