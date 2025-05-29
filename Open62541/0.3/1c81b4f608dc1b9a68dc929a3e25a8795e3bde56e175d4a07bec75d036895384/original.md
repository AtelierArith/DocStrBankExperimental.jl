```
UA_ViewAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    containsnoloops::Union{Nothing, Bool} = nothing,
    eventnotifier::Union{Nothing, UInt8} = nothing)::Ptr{UA_ViewAttributes}
```

generates a `UA_ViewAttributes` object. Memory for the object is allocated by C and needs to be cleaned up by calling `UA_ViewAttributes_delete(x)` after usage.

For keywords given as `nothing`, the respective default value is used, see `UA_ViewAttributes_default[]`

See also [`UA_WRITEMASK`](@ref), [`UA_USERWRITEMASK`](@ref) and [`UA_EVENTNOTIFIER`](@ref) for information on how to generate the respective keyword inputs.
