```
overapproximate(lm::LinearMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray},
                set_type::Type{<:LazySet}) where {N}
```

Decompose a lazy linear map of a Cartesian product array with a given set type while keeping the original block structure.

### Input

  * `lm`                    – lazy linear map of a Cartesian product array
  * `CartesianProductArray` – target set type
  * `set_type`              – set type for overapproximation

### Output

A `CartesianProductArray` representing the decomposed linear map.
