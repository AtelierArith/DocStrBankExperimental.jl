```
project(X::LazySet, block::AbstractVector{Int}, ε::Real, [n]::Int=dim(X);
        [kwargs...])
```

Project a set to a given block and set type with an error bound.

### Input

  * `X`     – set
  * `block` – block structure - a vector with the dimensions of interest
  * `ε`     – error bound for approximation
  * `n`     – (optional, default: `dim(X)`) ambient dimension of the set `X`

### Output

A set representing the epsilon-close approximation of the projection of `X`.

### Algorithm

1. Project the set `X` with `M⋅X`, where `M` is the identity matrix in the block

coordinates and zero otherwise.

2. Overapproximate the projected set with the given error bound `ε`.

The target set type is chosen automatically.
