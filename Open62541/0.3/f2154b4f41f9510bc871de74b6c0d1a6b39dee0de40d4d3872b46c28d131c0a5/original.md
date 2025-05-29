```
UA_VariableTypeAttributes_generate(; value::Union{Nothing, AbstractArray{T}, T} = nothing,
    displayname::AbstractString, description::AbstractString,
    localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    valuerank::Union{Nothing, Integer} = nothing,
    isabstract::Union{Nothing, Bool})::Ptr{UA_VariableTypeAttributes} where {T <: Union{Nothing, UA_NUMBER_TYPES, Complex{Float32}, Complex{Float64}, Rational{Int32}, Rational{UInt32}, AbstractString}}
```

generates a `UA_VariableTypeAttributes` object. Memory for the object is allocated by C and needs to be cleaned up by calling `UA_VariableTypeAttributes_delete(x)` after usage.

For keywords given as `nothing`, the respective default value is used, see `UA_VariableTypeAttributes_default[]`. If a default `value` is specified for the variabletype and nothing is given for keyword `valuerank`, then it is either set to `UA_VALUERANK_SCALAR` (if `value` is a scalar), or to the dimensionality of the supplied array (i.e., `N` for an AbstractArray{T,N}).

See also [`UA_WRITEMASK`](@ref), [`UA_USERWRITEMASK`](@ref) for information on how to generate the respective keyword inputs.
