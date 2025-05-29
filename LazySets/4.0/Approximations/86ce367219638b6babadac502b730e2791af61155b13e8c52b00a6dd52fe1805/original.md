```
project(S::LazySet,
        block::AbstractVector{Int},
        directions::Type{<:AbstractDirections},
        [n]::Int;
        [kwargs...]
       )
```

Project a high-dimensional set to a given block using direction vectors.

### Input

  * `S`          – set
  * `block`      – block structure - a vector with the dimensions of interest
  * `directions` – direction vectors
  * `n`          – (optional, default: `dim(S)`) ambient dimension of the set `S`

### Output

The polyhedral overapproximation of the projection of `S` in the given directions.
