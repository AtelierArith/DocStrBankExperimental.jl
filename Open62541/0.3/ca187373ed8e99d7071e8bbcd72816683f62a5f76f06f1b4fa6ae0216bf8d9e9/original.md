```
UA_VariableAttributes_generate(; value::Union{AbstractArray{T}, T},
    displayname::AbstractString, description::AbstractString,
    localization::AbstractString = "en-US",
    writemask::Union{Nothing, UInt32} = nothing,
    userwritemask::Union{Nothing, UInt32} = nothing,
    accesslevel::Union{Nothing, UInt8} = nothing,
    useraccesslevel::Union{Nothing, UInt8} = nothing,
    minimumsamplinginterval::Union{Nothing, Float64} = nothing,
    historizing::Union{Nothing, Bool} = nothing,
    valuerank::Union{Integer, Nothing} = nothing)::Ptr{UA_VariableAttributes} where {T <: Union{UA_NUMBER_TYPES, Complex{Float32}, Complex{Float64}, Rational{Int32}, Rational{UInt32}, AbstractString}}
```

generates a `UA_VariableAttributes` object. Memory for the object is allocated by C and needs to be cleaned up by calling `UA_VariableAttributes_delete(x)` after usage.

For keywords given as `nothing`, the respective default value is used, see `UA_VariableAttributes_default[]`. If nothing is given for keyword `valuerank`, then it is either set to `UA_VALUERANK_SCALAR` (if `value` is a scalar), or to the dimensionality of the supplied array (i.e., `N` for an AbstractArray{T,N}).

See also [`UA_WRITEMASK`](@ref), [`UA_USERWRITEMASK`](@ref), [`UA_ACCESSLEVEL`](@ref), and [`UA_USERACCESSLEVEL`](@ref) for information on how to generate the respective keyword inputs.
