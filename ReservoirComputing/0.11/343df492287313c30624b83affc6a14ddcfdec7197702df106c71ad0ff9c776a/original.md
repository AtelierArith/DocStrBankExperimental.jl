```
minimal_init([rng], [T], dims...;
    sampling_type=:bernoulli_sample!, weight=0.1, irrational=pi,
    start=1, p=0.5)
```

Create a layer matrix with uniform weights determined by `weight` [^rodan2010]. The sign difference is randomly determined by the `sampling` chosen.

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the matrix. Should follow `res_size x in_size`.

# Keyword arguments

  * `weight`: The weight used to fill the layer matrix. Default is 0.1.
  * `sampling_type`: Sampling that decides the distribution of `weight` negative numbers. If set to `:no_sample` the sign is unchanged. If set to `:bernoulli_sample!` then each `weight` can be positive with a probability set by `positive_prob`. If set to `:irrational_sample!` the `weight` is negative if the decimal number of the irrational number chosen is odd. If set to `:regular_sample!`, each weight will be assigned a negative sign after the chosen `strides`. `strides` can be a single number or an array. Default is `:no_sample`.
  * `positive_prob`: probability of the `weight` being positive when `sampling_type` is set to `:bernoulli_sample!`. Default is 0.5.
  * `irrational`: Irrational number whose decimals decide the sign of `weight`. Default is `pi`.
  * `start`: Which place after the decimal point the counting starts for the `irrational` sign counting. Default is 1.
  * `strides`: number of strides for assigning negative value to a weight. It can be an integer or an array. Default is 2.

# Examples

```jldoctest
julia> res_input = minimal_init(8, 3)
8×3 Matrix{Float32}:
  0.1  -0.1   0.1
 -0.1   0.1   0.1
 -0.1  -0.1   0.1
 -0.1  -0.1  -0.1
  0.1   0.1   0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1   0.1
  0.1  -0.1   0.1

julia> res_input = minimal_init(8, 3; sampling_type=:irrational)
8×3 Matrix{Float32}:
 -0.1   0.1  -0.1
  0.1  -0.1  -0.1
  0.1   0.1  -0.1
  0.1   0.1   0.1
 -0.1  -0.1  -0.1
  0.1   0.1   0.1
  0.1   0.1  -0.1
 -0.1   0.1  -0.1

julia> res_input = minimal_init(8, 3; p=0.1) # lower p -> more negative signs
8×3 Matrix{Float32}:
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
  0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1
 -0.1  -0.1  -0.1

julia> res_input = minimal_init(8, 3; p=0.8)# higher p -> more positive signs
8×3 Matrix{Float32}:
  0.1   0.1  0.1
 -0.1   0.1  0.1
 -0.1   0.1  0.1
  0.1   0.1  0.1
  0.1   0.1  0.1
  0.1  -0.1  0.1
 -0.1   0.1  0.1
  0.1   0.1  0.1
```

[^rodan2010]: Rodan, Ali, and Peter Tino. "Minimum complexity echo state network." IEEE transactions on neural networks 22.1 (2010): 131-144.
