```
double_cycle([rng], [T], dims...; 
    cycle_weight=0.1, second_cycle_weight=0.1,
    return_sparse=false)
```

Creates a double cycle reservoir [^fu2023].

# Arguments

  * `rng`: Random number generator. Default is `Utils.default_rng()` from WeightInitializers.
  * `T`: Type of the elements in the reservoir matrix. Default is `Float32`.
  * `dims`: Dimensions of the reservoir matrix.

# Keyword arguments

  * `cycle_weight`: Weight of the upper cycle connections in the reservoir matrix. Default is 0.1.
  * `second_cycle_weight`: Weight of the lower cycle connections in the reservoir matrix. Default is 0.1.
  * `return_sparse`: flag for returning a `sparse` matrix. Default is `false`.

# Examples

```jldoctest
julia> reservoir_matrix = double_cycle(5, 5; cycle_weight=0.1, second_cycle_weight=0.3)
5×5 Matrix{Float32}:
 0.0  0.3  0.0  0.0  0.3
 0.1  0.0  0.3  0.0  0.0
 0.0  0.1  0.0  0.3  0.0
 0.0  0.0  0.1  0.0  0.3
 0.1  0.0  0.0  0.1  0.0
```

[^fu2023]: Fu, Jun, et al. "A double-cycle echo state network topology for time series prediction." Chaos: An Interdisciplinary Journal of Nonlinear Science 33.9 (2023).
