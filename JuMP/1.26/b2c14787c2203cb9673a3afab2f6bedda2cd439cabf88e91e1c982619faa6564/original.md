```
direct_generic_model(
    value_type::Type{T},
    backend::MOI.ModelLike;
) where {T<:Real}
```

Return a new JuMP model using [`backend`](@ref) to store the model and solve it.

As opposed to the [`Model`](@ref) constructor, no cache of the model is stored outside of [`backend`](@ref) and no bridges are automatically applied to [`backend`](@ref).

## Notes

The absence of a cache reduces the memory footprint but, it is important to bear in mind the following implications of creating models using this *direct* mode:

  * When [`backend`](@ref) does not support an operation, such as modifying constraints or adding variables/constraints after solving, an error is thrown. For models created using the [`Model`](@ref) constructor, such situations can be dealt with by storing the modifications in a cache and loading them into the optimizer when `optimize!` is called.
  * No constraint bridging is supported by default.
  * The optimizer used cannot be changed the model is constructed.
  * The model created cannot be copied.
