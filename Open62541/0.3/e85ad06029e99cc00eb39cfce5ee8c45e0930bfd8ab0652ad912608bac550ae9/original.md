```
UA_MethodAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    executable::Union{Nothing, Bool} = nothing,
    userexecutable::Union{Nothing, Bool} = nothing)::Ptr{UA_MethodAttributes}
```

generates a `UA_MethodAttributes` object. Memory for the object is allocated by C and needs to be cleaned up by calling `UA_MethodAttributes_delete(x)` after usage.

For keywords given as `nothing`, the respective default value is used, see `UA_MethodAttributes_default[]`

See also [`UA_WRITEMASK`](@ref) and [`UA_USERWRITEMASK`](@ref) for information on how to generate the respective keyword inputs.
