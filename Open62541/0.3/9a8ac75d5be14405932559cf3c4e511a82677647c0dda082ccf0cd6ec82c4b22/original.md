```
UA_ReferenceTypeAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    isabstract::Union{Nothing, Bool} = nothing
    symmetric::Union{Nothing, Bool} = nothing,
    inversename::Union{Nothing, AbstractString} = nothing)::Ptr{UA_ReferenceTypeAttributes}
```

generates a `UA_ReferenceTypeAttributes` object. Memory for the object is allocated by C and needs to be cleaned up by calling `UA_ReferenceTypeAttributes_delete(x)` after usage.

For keywords given as `nothing`, the respective default value is used, see `UA_ReferenceTypeAttributes_default[]`

See also [`UA_WRITEMASK`](@ref) and [`UA_USERWRITEMASK`](@ref) for information on how to generate the respective keyword inputs.
