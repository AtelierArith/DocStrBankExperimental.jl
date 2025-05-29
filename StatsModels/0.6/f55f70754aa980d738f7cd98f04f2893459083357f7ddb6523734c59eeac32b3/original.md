```
ConstantTerm{T<:Number} <: AbstractTerm
```

Represents a literal number in a formula.  By default will be converted to [`InterceptTerm`] by [`apply_schema`](@ref).

# Fields

  * `n::T`: The number represented by this term.
