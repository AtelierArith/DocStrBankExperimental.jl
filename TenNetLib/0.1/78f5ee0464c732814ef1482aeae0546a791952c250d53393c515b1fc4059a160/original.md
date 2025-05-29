```
function isometrize!(ttn::TTN, node::Int2; kwargs...)
```

Moves the isometry / orthogonality center of the TTN to a new center `node`. If the TTN does not have proper orthoginality center, Isometrizes the TTN from scratch.

#### Named arguments and their default values.

  * `normalize::Bool = true`: Whether to normalize the TTN afterwards.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
