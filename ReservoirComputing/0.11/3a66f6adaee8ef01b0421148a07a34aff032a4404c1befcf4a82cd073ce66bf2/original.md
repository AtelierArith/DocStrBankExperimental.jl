```
selfloop_forward_connection([rng], [T], dims...; 
    weight=0.1, selfloop_weight=0.1,
    return_sparse=false, selfloop_kwargs=(),
    delay_kwargs=())
```

Creates a reservoir based on a forward connection of weights between even nodes with the addition of self loops [^elsarraj2019].

This architecture is referred to as TP4 in the original paper.

# Equations

$$
W_{i,j} =
\begin{cases}
    ll, & \text{if } i = j \text{ for } i = 1 \dots N \\
    r, & \text{if } j = i - 2 \text{ for } i = 3 \dots N \\
    0, & \text{otherwise}
\end{cases}
$$

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `weight`: Weight of the cycle connections in the reservoir matrix. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the cycle you want to populate. Default is 0.1.
  * `selfloop_weight`: Weight of the self loops in the reservoir matrix. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the diagonal you want to populate. Default is 0.1.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.
  * `delay_kwargs` and `selfloop_kwargs`: named tuples that control the kwargs for the  delay line weight and self loop weights respectively. The kwargs are as follows:

      * `sampling_type`: Sampling that decides the distribution of `weight` negative numbers.   If set to `:no_sample` the sign is unchanged. If set to `:bernoulli_sample!` then each   `weight` can be positive with a probability set by `positive_prob`. If set to   `:irrational_sample!` the `weight` is negative if the decimal number of the   irrational number chosen is odd. If set to `:regular_sample!`, each weight will be   assigned a negative sign after the chosen `strides`. `strides` can be a single   number or an array. Default is `:no_sample`.

          * `positive_prob`: probability of the `weight` being positive when `sampling_type` is set to `:bernoulli_sample!`. Default is 0.5.
          * `irrational`: Irrational number whose decimals decide the sign of `weight`. Default is `pi`.
          * `start`: Which place after the decimal point the counting starts for the `irrational` sign counting. Default is 1.
          * `strides`: number of strides for assigning negative value to a weight. It can be an integer or an array. Default is 2.

# Examples

```jldoctest
julia> reservoir_matrix = selfloop_forward_connection(5, 5)
5×5 Matrix{Float32}:
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.0  0.0  0.0
 0.1  0.0  0.1  0.0  0.0
 0.0  0.1  0.0  0.1  0.0
 0.0  0.0  0.1  0.0  0.1

julia> reservoir_matrix = selfloop_forward_connection(5, 5; weight=0.5)
5×5 Matrix{Float32}:
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.0  0.0  0.0
 0.5  0.0  0.1  0.0  0.0
 0.0  0.5  0.0  0.1  0.0
 0.0  0.0  0.5  0.0  0.1
```

[^elsarraj2019]: Elsarraj, Duaa, et al. "Demystifying echo state network with deterministic simple topologies." International Journal of Computational Science and Engineering 19.3 (2019): 407-417.
