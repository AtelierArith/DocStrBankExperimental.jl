```
identityoperator(a::Basis[, b::Basis])
identityoperator(::Type{<:AbstractOperator}, a::Basis[, b::Basis])
identityoperator(::Type{<:Number}, a::Basis[, b::Basis])
identityoperator(::Type{<:AbstractOperator}, ::Type{<:Number}, a::Basis[, b::Basis])
```

Return an identityoperator in the given bases. One can optionally specify the container type which has to a subtype of [`AbstractOperator`](@ref) as well as the number type to be used in the identity matrix.
