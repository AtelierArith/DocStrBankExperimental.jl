```
generate_and_add_supports!(prefs::AbstractArray{<:DependentParameterRef},
                           domain::InfiniteArrayDomain,
                           [method::Type{<:AbstractSupportLabel}];
                           [num_supports::Int = DefaultNumSupports])::Nothing
```

Generate supports for `prefs` via [`generate_support_values`](@ref) and add them to `pref`. This is intended as an extendable internal method for [`fill_in_supports!`](@ref fill_in_supports!(::AbstractArray{<:DependentParameterRef})). Most extensions that employ user-defined infinite domains can typically enable this by extending [`generate_support_values`](@ref). However, in some cases it may be necessary to extend this when more complex operations need to take place then just adding supports to a set of infinite parameters. Errors if the infinite domain type is not recognized.
