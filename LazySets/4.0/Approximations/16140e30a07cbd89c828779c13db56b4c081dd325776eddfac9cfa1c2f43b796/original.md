```
overapproximate(lm::LinearMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray},
                dir::Type{<:AbstractDirections}) where {N}
```

Decompose a lazy linear map of a Cartesian product array with template directions while keeping the original block structure.

### Input

  * `lm`                    – lazy linear map of a Cartesian product array
  * `CartesianProductArray` – target set type
  * `dir`                   – template directions for overapproximation

### Output

A `CartesianProductArray` representing the decomposed linear map.
