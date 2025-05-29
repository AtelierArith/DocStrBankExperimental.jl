```
project(X::LazySet, block::AbstractVector{Int},
        set_type_and_precision::Pair{<:UnionAll,<:Real}, [n]::Int=dim(X);
        [kwargs...])
```

Project a set to a given block and set type with a certified error bound.

### Input

  * `X`     – set
  * `block` – block structure - a vector with the dimensions of interest
  * `set_type_and_precision` – pair `(T, ε)` of a target set type `T` and an                             error bound `ε` for approximation
  * `n`     – (optional, default: `dim(X)`) ambient dimension of the set `X`

### Output

A set representing the epsilon-close approximation of the projection of `X`.

### Notes

Currently we only support `HPolygon` as set type, which implies that the set must be two-dimensional.

### Algorithm

1. Project the set `X` with `M⋅X`, where `M` is the identity matrix in the block

coordinates and zero otherwise.

2. Overapproximate the projected set with the given error bound `ε`.
