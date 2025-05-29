```
function isometrize_full!(ttn::TTN, node::Int2; kwargs...)
```

Isometrizes the TTN from scratch with respect to the orthogonality center `node::Int2`.

#### Named arguments and their default values.

  * `normalize::Bool = true`: Whether to normalize the TTN afterwards.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
