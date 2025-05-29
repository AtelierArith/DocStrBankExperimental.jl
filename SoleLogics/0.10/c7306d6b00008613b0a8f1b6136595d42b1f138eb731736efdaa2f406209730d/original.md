```
struct Literal{T<:SyntaxLeaf} <: SyntaxStructure
    ispos::Bool
    prop::T
end
```

An atom, or its negation.

See also [`CNF`](@ref), [`DNF`](@ref), [`SyntaxStructure`](@ref).
