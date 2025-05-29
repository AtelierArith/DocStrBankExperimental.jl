```
struct StorageValueCut
```

A `StorageValueCut` represents a cutting hyperplane that puts an upper bound on the value of the stored resource at the end of the optimization horizon.

## Fields

  * **`id::Any`** is the name/identifier of the `StorageValueCut`.
  * **`coeffs::Vector{<:ElementValue}`** are the cut coefficients associated with the level of the given `Storage` nodes. They can also be provided as `Dict{<:Storage{<:Accumulating}, <:Real}`.
  * **`rhs::Real`** is the cut right hand side constant.
