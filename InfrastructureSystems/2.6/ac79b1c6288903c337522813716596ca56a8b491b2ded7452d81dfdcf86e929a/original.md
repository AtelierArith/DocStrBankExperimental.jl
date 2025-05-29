```julia
get_supplemental_attributes(
    filter_func::Function,
    _::Type{T<:InfrastructureSystems.SupplementalAttribute},
    mgr::InfrastructureSystems.SupplementalAttributeManager
) -> InfrastructureSystems.FlattenIteratorWrapper{T, I} where {T<:InfrastructureSystems.SupplementalAttribute, I<:(Vector)}

```

Returns an iterator of supplemental_attributes. T can be concrete or abstract. Call collect on the result if an array is desired.

# Arguments

  * `T`: supplemental_attribute type
  * `mgr::SupplementalAttributeManager`: SupplementalAttributeManager in the system
  * `filter_func::Union{Nothing, Function} = nothing`: Optional function that accepts a component of type T and returns a Bool. Apply this function to each component and only return components where the result is true.
