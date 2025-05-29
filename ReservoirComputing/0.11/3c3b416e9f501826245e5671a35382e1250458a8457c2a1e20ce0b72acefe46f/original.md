```
cycle_jumps([rng], [T], dims...; 
    cycle_weight=0.1, jump_weight=0.1, jump_size=3, return_sparse=false,
    cycle_kwargs=(), jump_kwargs=())
```

Create a cycle jumps reservoir [^Rodan2012].

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `cycle_weight`:  The weight of cycle connections. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the cycle you want to populate. Default is 0.1.
  * `jump_weight`: The weight of jump connections. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the jumps you want to populate. Default is 0.1.
  * `jump_size`:  The number of steps between jump connections. Default is 3.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.
  * `cycle_kwargs` and `jump_kwargs`: named tuples that control the kwargs for the cycle and jump weights respectively. The kwargs are as follows:

      * `sampling_type`: Sampling that decides the distribution of `weight` negative numbers. If set to `:no_sample` the sign is unchanged. If set to `:bernoulli_sample!` then each `weight` can be positive with a probability set by `positive_prob`. If set to `:irrational_sample!` the `weight` is negative if the decimal number of the irrational number chosen is odd. If set to `:regular_sample!`, each weight will be assigned a negative sign after the chosen `strides`. `strides` can be a single number or an array. Default is `:no_sample`.
      * `positive_prob`: probability of the `weight` being positive when `sampling_type` is set to `:bernoulli_sample!`. Default is 0.5.
      * `irrational`: Irrational number whose decimals decide the sign of `weight`. Default is `pi`.
      * `start`: Which place after the decimal point the counting starts for the `irrational` sign counting. Default is 1.
      * `strides`: number of strides for assigning negative value to a weight. It can be an integer or an array. Default is 2.

# Examples

```jldoctest
julia> res_matrix = cycle_jumps(5, 5)
5×5 Matrix{Float32}:
 0.0  0.0  0.0  0.1  0.1
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.0  0.0  0.0
 0.1  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.0

julia> res_matrix = cycle_jumps(5, 5; jump_size=2)
5×5 Matrix{Float32}:
 0.0  0.0  0.1  0.0  0.1
 0.1  0.0  0.0  0.0  0.0
 0.1  0.1  0.0  0.0  0.1
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.1  0.1  0.0
```

[^rodan2012]: Rodan, Ali, and Peter Tiňo. "Simple deterministically constructed cycle reservoirs with regular jumps." Neural computation 24.7 (2012): 1822-1852.
