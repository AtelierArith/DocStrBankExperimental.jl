```
UA_ObjectAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    eventnotifier::Union{Nothing, UInt8} = nothing)::Ptr{UA_ObjectAttributes}
```

generates a `UA_ObjectAttributes` object. Memory for the object is allocated by C and needs to be cleaned up by calling `UA_ObjectAttributes_delete(x)` after usage.

For keywords given as `nothing`, the respective default value is used, see `UA_ObjectAttributes_default[]`

See also [`UA_WRITEMASK`](@ref), [`UA_USERWRITEMASK`](@ref), [`UA_EVENTNOTIFIER`](@ref) for information on how to generate the respective keyword inputs.
