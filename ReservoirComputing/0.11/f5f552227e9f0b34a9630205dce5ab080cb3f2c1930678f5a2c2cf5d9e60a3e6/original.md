```
selfloop_feedback_cycle([rng], [T], dims...; 
    cycle_weight=0.1, selfloop_weight=0.1,
    return_sparse=false)
```

Creates a cycle reservoir with feedback connections on even neurons and self loops on odd neurons [^elsarraj2019].

This architecture is referred to as TP2 in the original paper.

# Equations

$$
W_{i,j} =
\begin{cases}
    r, & \text{if } j = i - 1 \text{ for } i = 2 \dots N \\
    r, & \text{if } i = 1, j = N \\
    ll, & \text{if } i = j \text{ and } i \text{ is odd} \\
    r, & \text{if } j = i + 1 \text{ and } i \text{ is even}, i \neq N \\
    0, & \text{otherwise}
\end{cases}
$$

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `cycle_weight`: Weight of the cycle connections in the reservoir matrix. This can be provided as a single value or an array. In case it is provided as an array please make sure that the lenght of the array matches the lenght of the cycle you want to populate. Default is 0.1.
  * `selfloop_weight`: Weight of the self loops in the reservoir matrix. Default is 0.1.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.

# Examples

```jldoctest
julia> reservoir_matrix = selfloop_feedback_cycle(5, 5)
5×5 Matrix{Float32}:
 0.1  0.1  0.0  0.0  0.1
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.1  0.1  0.0
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.1

julia> reservoir_matrix = selfloop_feedback_cycle(5, 5; self_loop_weight=0.5)
5×5 Matrix{Float32}:
 0.5  0.1  0.0  0.0  0.1
 0.1  0.0  0.0  0.0  0.0
 0.0  0.1  0.5  0.1  0.0
 0.0  0.0  0.1  0.0  0.0
 0.0  0.0  0.0  0.1  0.5
```

[^elsarraj2019]: Elsarraj, Duaa, et al. "Demystifying echo state network with deterministic simple topologies." International Journal of Computational Science and Engineering 19.3 (2019): 407-417.
