```
delay_line([rng], [T], dims...;
    weight=0.1, return_sparse=false,
    kwargs...)
```

Create and return a delay line reservoir matrix [^rodan2010].

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `weight`: Determines the value of all connections in the reservoir. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the sub-diagonal you want to populate. Default is 0.1.
  * `shift`: delay line shift. Default is 1.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.
  * `sampling_type`: Sampling that decides the distribution of `weight` negative numbers. If set to `:no_sample` the sign is unchanged. If set to `:bernoulli_sample!` then each `weight` can be positive with a probability set by `positive_prob`. If set to `:irrational_sample!` the `weight` is negative if the decimal number of the irrational number chosen is odd. If set to `:regular_sample!`, each weight will be assigned a negative sign after the chosen `strides`. `strides` can be a single number or an array. Default is `:no_sample`.
  * `positive_prob`: probability of the `weight` being positive when `sampling_type` is set to `:bernoulli_sample!`. Default is 0.5.
  * `irrational`: Irrational number whose decimals decide the sign of `weight`. Default is `pi`.
  * `start`: Which place after the decimal point the counting starts for the `irrational` sign counting. Default is 1.
  * `strides`: number of strides for assigning negative value to a weight. It can be an integer or an array. Default is 2.

# Examples

```jldoctest
julia> res_matrix = delay_line(5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.0  0.0  0.0
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.0

julia> res_matrix = delay_line(5, 5; weight=1)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.0  0.0
 1.0  0.0  0.0  0.0  0.0
 0.0  1.0  0.0  0.0  0.0
 0.0  0.0  1.0  0.0  0.0
 0.0  0.0  0.0  1.0  0.0
```

[^rodan2010]: Rodan, Ali, and Peter Tino. "Minimum complexity echo state network." IEEE transactions on neural networks 22.1 (2010): 131-144.
