```
project(X::LazySet, block::AbstractVector{Int}, set_type::Type{<:LazySet},
        [n]::Int=dim(X); [kwargs...])
```

Project a set to a given block and set type, possibly involving an overapproximation.

### Input

  * `X`        – set
  * `block`    – block structure - a vector with the dimensions of interest
  * `set_type` – target set type
  * `n`        – (optional, default: `dim(X)`) ambient dimension of the set `X`

### Output

A set of type `set_type` representing an overapproximation of the projection of `X`.

### Algorithm

1. Project the set `X` with `M⋅X`, where `M` is the identity matrix in the block

coordinates and zero otherwise.

2. Overapproximate the projected set using `overapproximate` and `set_type`.
