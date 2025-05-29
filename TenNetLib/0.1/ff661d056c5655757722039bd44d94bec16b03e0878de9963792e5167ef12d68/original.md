```
function moveisometry_to_next!(ttn::TTN, node1::Int2, node2::Int2; kwargs...)
```

Moves the isometry / orthogonality center of the TTN from `node1::Int2` to the neighboring `node2::Int`. `node1` and `node2` must be neighboring nodes. `node1` must be the orthogonality center unless `ignore_orthocenter = true`.

**Note**: Does not normalize the TTN afterwards.

#### Named arguments and their default values.

  * `ignore_orthocenter::Bool` = false: If set to `true`, `node1` is not required to be the orthogonality center.
  * `maxdim::Int = typemax(Int)`: Maximum bond dimension after SVD truncation.
  * `mindim::Int = 1`: Minimum bond dimension after SVD truncation.
  * `cutoff::Float64 = Float64_threshold()`: Cutoff for SVD truncation.
  * `svd_alg::String = "divide_and_conquer"`.
