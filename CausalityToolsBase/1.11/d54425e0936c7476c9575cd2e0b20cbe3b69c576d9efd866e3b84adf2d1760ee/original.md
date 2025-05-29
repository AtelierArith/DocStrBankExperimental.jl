```
optimal_dimension(v, τ; dims = 2:8; method = "fnn"; kwargs...)
```

Estimate the optimal embedding dimension for `v`.

## Arguments

  * **`v`**: The data series for which to estimate the embedding dimension.
  * **`τ`**: The embedding lag.
  * **`dims`**: Dimensions to probe for the optimal dimension.

## Keyword arguments

  * **`method`**: Either "fnn" (Kennel's false nearest neighbors method),   "afnn" (Cao's average false nearest neighbors method) or "f1nn" (Krakovská's   false first nearest neighbors method). See the source code for   `DelayEmbeddings.estimate_dimension` for more details.
  * **`rtol`**: Tolerance `rtol` in Kennel's algorithms. See [`DelayEmbeddings.fnn`](https://github.com/JuliaDynamics/DelayEmbeddings.jl/blob/master/src/estimate_dimension.jl)    source code for more details.
  * **`atol`**: Tolerance `rtol` in Kennel's algorithms. See [`DelayEmbeddings.fnn`](https://github.com/JuliaDynamics/DelayEmbeddings.jl/blob/master/src/estimate_dimension.jl)   source code for more details.
