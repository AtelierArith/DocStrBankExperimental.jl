```
AbstractData
```

Defines a Data type that can be composed with an [`AbstractSpace`](@ref) to form a Field

Concrete subtypes should implement:

[`allocate_values`](@ref), [`check_values`](@ref), [`zero_values!`](@ref), [`dof_values`](@ref)

If the subtype needs to provide values for a numerical solver (eg as a state variable), it also needs to implement:

[`init_values!`](@ref), [`copyfieldto!`](@ref), [`copytofield!`](@ref), [`add_field!`](@ref), [`add_field_vec!`](@ref)

If the subtype has a representation as components, it should implement: [`num_components`](@ref), [`get_components`](@ref)

If the subtype needs to provide a thread-safe atomic addition operation eg to provide scalar accumulator variables for Domain totals with a tiled model, it should implement [`atomic_add!`](@ref) for the field values.
