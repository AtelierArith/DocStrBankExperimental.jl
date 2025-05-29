```
struct Literal{T<:SyntaxLeaf} <: AbstractSyntaxStructure
    ispos::Bool
    prop::T
end
```

An atom, or its negation.

See also [`CNF`](@ref), [`DNF`](@ref), [`AbstractSyntaxStructure`](@ref).
