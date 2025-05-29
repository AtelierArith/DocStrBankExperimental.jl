```
delay_line_backward([rng], [T], dims...;
    weight=0.1, fb_weight=0.2, return_sparse=false,
    delay_kwargs=(), fb_kwargs=())
```

Create a delay line backward reservoir with the specified by `dims` and weights. Creates a matrix with backward connections as described in [^rodan2010].

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `weight`: The weight determines the absolute value of forward connections in the reservoir. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the sub-diagonal you want to populate. Default is 0.1
  * `fb_weight`: Determines the absolute value of backward connections in the reservoir. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the sub-diagonal you want to populate. Default is 0.2.
  * `fb_shift`: How far the backward connection will be from the diagonal. Default is 2.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.
  * `delay_kwargs` and `fb_kwargs`: named tuples that control the kwargs for the delay line weight and feedback weights respectively. The kwargs are as follows:

      * `sampling_type`: Sampling that decides the distribution of `weight` negative numbers. If set to `:no_sample` the sign is unchanged. If set to `:bernoulli_sample!` then each `weight` can be positive with a probability set by `positive_prob`. If set to `:irrational_sample!` the `weight` is negative if the decimal number of the irrational number chosen is odd. If set to `:regular_sample!`, each weight will be assigned a negative sign after the chosen `strides`. `strides` can be a single number or an array. Default is `:no_sample`.
      * `positive_prob`: probability of the `weight` being positive when `sampling_type` is set to `:bernoulli_sample!`. Default is 0.5.
      * `irrational`: Irrational number whose decimals decide the sign of `weight`. Default is `pi`.
      * `start`: Which place after the decimal point the counting starts for the `irrational` sign counting. Default is 1.
      * `strides`: number of strides for assigning negative value to a weight. It can be an integer or an array. Default is 2.

# Examples

```jldoctest
julia> res_matrix = delay_line_backward(5, 5)
5×5 Matrix{Float32}:
 0.0  0.2  0.0  0.0  0.0
 0.1  0.0  0.2  0.0  0.0
 0.0  0.1  0.0  0.2  0.0
 0.0  0.0  0.1  0.0  0.2
 0.0  0.0  0.0  0.1  0.0

julia> res_matrix = delay_line_backward(Float16, 5, 5)
5×5 Matrix{Float16}:
 0.0  0.2  0.0  0.0  0.0
 0.1  0.0  0.2  0.0  0.0
 0.0  0.1  0.0  0.2  0.0
 0.0  0.0  0.1  0.0  0.2
 0.0  0.0  0.0  0.1  0.0
```

[^rodan2010]: Rodan, Ali, and Peter Tino. "Minimum complexity echo state network." IEEE transactions on neural networks 22.1 (2010): 131-144.
