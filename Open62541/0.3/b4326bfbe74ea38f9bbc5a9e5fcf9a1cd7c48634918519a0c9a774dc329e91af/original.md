```
UA_DataTypeAttributes_generate(; displayname::AbstractString,
    description::AbstractString, localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    isabstract::Union{Nothing, Bool} = nothing)::Ptr{UA_DataTypeAttributes}
```

generates a `UA_DataTypeAttributes` object. Memory for the object is allocated by C and needs to be cleaned up by calling `UA_DataTypeAttributes_delete(x)` after usage.

For keywords given as `nothing`, the respective default value is used, see `UA_DataTypeAttributes_default[]`

See also [`UA_WRITEMASK`](@ref) and [`UA_USERWRITEMASK`](@ref) for information on how to generate the respective keyword inputs.
