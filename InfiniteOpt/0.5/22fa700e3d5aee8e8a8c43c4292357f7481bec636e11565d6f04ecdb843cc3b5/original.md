```
generate_and_add_supports!(pref::IndependentParameterRef,
                           domain::AbstractInfiniteDomain,
                           [method::Type{<:AbstractSupportLabel}];
                           [num_supports::Int = DefaultNumSupports])::Nothing
```

Generate supports for independent parameter `pref` via [`generate_support_values`](@ref) and add them to `pref`. This is intended as an extendable internal method for [`fill_in_supports!`](@ref fill_in_supports!(::IndependentParameterRef)). Most extensions that empoy user-defined infinite domains can typically enable this by extending [`generate_support_values`](@ref). Errors if the infinite domain type is not recognized.
