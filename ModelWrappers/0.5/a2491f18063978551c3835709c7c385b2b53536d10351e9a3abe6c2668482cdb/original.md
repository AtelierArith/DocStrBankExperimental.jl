```julia
struct FlattenDefault{T<:AbstractFloat, F<:ModelWrappers.FlattenTypes}
```

Default arguments for flatten function.

# Fields

  * `output::Type{T} where T<:AbstractFloat`: Type of flatten output
  * `flattentype::ModelWrappers.FlattenTypes`: Determines if all inputs are flattened (FlattenAll) or only continuous values (FlattenContinuous).
