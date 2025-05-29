```
struct TransitionMatrix{S, C}
```

A transition probability matrix with [`Stochasticity`](@ref) `S` and [`Connectivity`](@ref) `C`.

### Fields

  * `P`: The transition probability `Matrix` itself.
  * `stochasticity`: `S`
  * `connectivity`: `C`

### Constructors

```
TransitionMatrix(P_size; n_zeros = 0, normalize = true, seed = 1234)
```

Construct a randomly generated transition matrix.

Arguments 

  * `P_size`: The number of rows (== columns) of the matrix.

Optional Arguments 

  * `n_zeros`: This many zeros will be placed in the matrix at random. If this results in a row of the matrix having all zeros, a `1` will be placed randomly in that row.
  * `normalize`: Whether to normalize the row sums of the resulting matrix.
  * `seed`: A seed for reproducible randomness.

# 

```
TransitionMatrix(P)
```

Construct a `TransitionMatrix` from a matrix `P`. The properties of `P` are inferred automatically.

Arguments 

  * `P`: The transition matrix.
