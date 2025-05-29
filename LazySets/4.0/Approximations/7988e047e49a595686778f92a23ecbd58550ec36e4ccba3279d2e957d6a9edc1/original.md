```
overapproximate(lm::LinearMap{N, <:CartesianProductArray},
                ::Type{<:CartesianProductArray{N, S}}
               ) where {N, S<:LazySet}
```

Decompose a lazy linear map of a Cartesian product array while keeping the original block structure.

### Input

  * `lm`                    – lazy linear map of Cartesian product array
  * `CartesianProductArray` – target set type

### Output

A `CartesianProductArray` representing the decomposed linear map.
