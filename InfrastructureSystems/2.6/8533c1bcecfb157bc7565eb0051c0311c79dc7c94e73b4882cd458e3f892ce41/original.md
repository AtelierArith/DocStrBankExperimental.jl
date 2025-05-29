```julia
get_supplemental_attributes(
    _::Type{T<:InfrastructureSystems.SupplementalAttribute},
    component::InfrastructureSystems.InfrastructureSystemsComponent
) -> Any

```

Return a Vector of supplemental_attributes. T can be concrete or abstract.

# Arguments

  * `T`: supplemental_attribute type
  * `supplemental_attributes::SupplementalAttributes`: SupplementalAttributes in the system
  * `filter_func::Union{Nothing, Function} = nothing`: Optional function that accepts a component of type T and returns a Bool. Apply this function to each component and only return components where the result is true.
