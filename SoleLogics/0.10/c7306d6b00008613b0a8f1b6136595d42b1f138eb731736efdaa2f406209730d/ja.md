```
struct Literal{T<:SyntaxLeaf} <: SyntaxStructure
    ispos::Bool
    prop::T
end
```

原子、またはその否定。

関連項目としては [`CNF`](@ref)、[`DNF`](@ref)、[`SyntaxStructure`](@ref) があります。
