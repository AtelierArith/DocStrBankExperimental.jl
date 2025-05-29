```
struct Literal{T<:SyntaxLeaf} <: AbstractSyntaxStructure
    ispos::Bool
    prop::T
end
```

原子、またはその否定。

関連項目としては [`CNF`](@ref)、[`DNF`](@ref)、[`AbstractSyntaxStructure`](@ref) を参照してください。
