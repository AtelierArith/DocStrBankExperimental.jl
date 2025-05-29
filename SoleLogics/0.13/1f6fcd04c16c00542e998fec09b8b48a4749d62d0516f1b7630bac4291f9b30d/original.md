```
struct Literal{T<:SyntaxLeaf} <: SyntaxStructure
    ispos::Bool
    atom::T
end
```

An atom, or its negation.

See also [`CNF`](@ref), [`DNF`](@ref), [`SyntaxStructure`](@ref).
