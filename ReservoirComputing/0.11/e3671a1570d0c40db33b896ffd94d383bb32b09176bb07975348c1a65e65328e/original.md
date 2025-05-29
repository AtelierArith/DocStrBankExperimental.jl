```
self_loop!([rng], reservoir_matrix, weight, jump_size;
    sampling_type=:no_sample, irrational=pi, start=1,
    positive_prob=0.5)
```

Adds jumps to a given `reservoir_matrix` with chosen `weight` and determined `jump_size`. `weight` can be either a number or an array.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `reservoir_matrix`: matrix to be changed.
  * `weight`: weight to add as a self loop. Can be either a single number or an array.

# Keyword arguments

  * `sampling_type`: Sampling that decides the distribution of `weight` negative numbers. If set to `:no_sample` the sign is unchanged. If set to `:bernoulli_sample!` then each `weight` can be positive with a probability set by `positive_prob`. If set to `:irrational_sample!` the `weight` is negative if the decimal number of the irrational number chosen is odd. If set to `:regular_sample!`, each weight will be assigned a negative sign after the chosen `strides`. `strides` can be a single number or an array. Default is `:no_sample`.
  * `positive_prob`: probability of the `weight` being positive when `sampling_type` is set to `:bernoulli_sample!`. Default is 0.5.
  * `irrational`: Irrational number whose decimals decide the sign of `weight`. Default is `pi`.
  * `start`: Which place after the decimal point the counting starts for the `irrational` sign counting. Default is 1.
  * `strides`: number of strides for assigning negative value to a weight. It can be an integer or an array. Default is 2.

# Examples

```jldoctest
julia> matrix = zeros(Float32, 5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0
 0.0  0.0  0.0  0.0  0.0

julia> self_loop!(matrix, 1.0)
5×5 Matrix{Float32}:
  1.0  0.0   0.0   0.0   0.0
  0.0  1.0   0.0   0.0   0.0
  0.0  0.0   1.0   0.0   0.0
  0.0  0.0   0.0   1.0   0.0
  0.0  0.0   0.0   0.0   1.0
```
