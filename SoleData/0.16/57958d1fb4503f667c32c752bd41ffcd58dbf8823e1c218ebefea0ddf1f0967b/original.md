```
parsefeature(FT::Type{<:AbstractFeature}, expr::AbstractString; kwargs...)
```

Parse a feature of type `FT` from its [`syntaxstring`](@ref) representation. Depending on `FT`, specifying keyword arguments such as `featvaltype::Type` may be required or recommended.

See also [`parsecondition`](@ref).
