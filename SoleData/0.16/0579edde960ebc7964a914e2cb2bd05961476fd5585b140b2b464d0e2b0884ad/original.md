```
parsecondition(C::Type{<:AbstractCondition}, expr::AbstractString; kwargs...)
```

Parse a condition of type `C` from its [`syntaxstring`](@ref) representation. Depending on `C`, specifying keyword arguments such as `featuretype::Type{<:AbstractFeature}`, and `featvaltype::Type` may be required or recommended.

See also [`parsefeature`](@ref).
