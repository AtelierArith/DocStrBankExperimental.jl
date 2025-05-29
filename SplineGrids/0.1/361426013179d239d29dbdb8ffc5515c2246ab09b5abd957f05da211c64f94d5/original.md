```
mult!(
    Y::V,
    As::NTuple{<:RefinementMatrix{Tv}, N},
    B::V,
    dims_refinement::NTuple{<:Integer, N})::Nothing where {Tv, V <: AbstractArray{Tv}, N}
```

'left-multiply' the array B by every refinement matrix along the specified dimension.

## Inputs

  * `Y`: The target array of the multiplication
  * `As`: The refinement matrices `Y` will be multiplied by
  * `B`: The array that will be multiplied by the refinement matrices
  * `dims_refinement`: The dimension along which the refinement matrix multiplication will take place for each matrix
