```
weighted_minimal([rng], [T], dims...;
    weight=0.1, return_sparse=false,
    sampling_type=:no_sample)
```

Create and return a minimal weighted input layer matrix. This initializer generates a weighted input matrix with equal, deterministic elements in the same construction as [`weighted_minimal]`(@ref), inspired by [^lu2017].

Please note that this initializer computes its own reservoir size! If the computed reservoir size is different than the provided one it will raise a warning.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`.

# Keyword arguments

  * `weight`: The value for all the weights in the input matrix. Defaults to `0.1`.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.
  * `sampling_type`: Sampling that decides the distribution of `weight` negative numbers. If set to `:no_sample` the sign is unchanged. If set to `:bernoulli_sample!` then each `weight` can be positive with a probability set by `positive_prob`. If set to `:irrational_sample!` the `weight` is negative if the decimal number of the irrational number chosen is odd. If set to `:regular_sample!`, each weight will be assigned a negative sign after the chosen `strides`. `strides` can be a single number or an array. Default is `:no_sample`.
  * `positive_prob`: probability of the `weight` being positive when `sampling_type` is set to `:bernoulli_sample!`. Default is 0.5.
  * `irrational`: Irrational number whose decimals decide the sign of `weight`. Default is `pi`.
  * `start`: Which place after the decimal point the counting starts for the `irrational` sign counting. Default is 1.
  * `strides`: number of strides for assigning negative value to a weight. It can be an integer or an array. Default is 2.

# Examples

```jldoctest
julia> res_input = weighted_minimal(8, 3)
┌ Warning: Reservoir size has changed!
│ 
│     Computed reservoir size (6) does not equal the provided reservoir size (8). 
│  
│     Using computed value (6). Make sure to modify the reservoir initializer accordingly. 
│ 
└ @ ReservoirComputing ~/.julia/dev/ReservoirComputing/src/esn/esn_inits.jl:159
6×3 Matrix{Float32}:
 0.1  0.0  0.0
 0.1  0.0  0.0
 0.0  0.1  0.0
 0.0  0.1  0.0
 0.0  0.0  0.1
 0.0  0.0  0.1

julia> res_input = weighted_minimal(9, 3; weight=0.99)
9×3 Matrix{Float32}:
 0.99  0.0   0.0
 0.99  0.0   0.0
 0.99  0.0   0.0
 0.0   0.99  0.0
 0.0   0.99  0.0
 0.0   0.99  0.0
 0.0   0.0   0.99
 0.0   0.0   0.99
 0.0   0.0   0.99

julia> res_input = weighted_minimal(9, 3; sampling_type=:bernoulli_sample!)
9×3 Matrix{Float32}:
  0.1  -0.0  -0.0
 -0.1  -0.0  -0.0
  0.1  -0.0   0.0
 -0.0   0.1   0.0
  0.0   0.1  -0.0
  0.0   0.1   0.0
 -0.0  -0.0  -0.1
 -0.0  -0.0   0.1
  0.0  -0.0   0.1
```

[^lu2017]: Lu, Zhixin, et al. "Reservoir observers: Model-free inference of unmeasured variables in chaotic systems." Chaos: An Interdisciplinary Journal of Nonlinear Science 27.4 (2017): 041102.
