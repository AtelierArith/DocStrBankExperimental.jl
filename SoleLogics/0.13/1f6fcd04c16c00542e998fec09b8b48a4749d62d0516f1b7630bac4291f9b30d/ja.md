```
struct Literal{T<:SyntaxLeaf} <: SyntaxStructure
    ispos::Bool
    atom::T
end
```

原子またはその否定。

関連情報としては [`CNF`](@ref), [`DNF`](@ref), [`SyntaxStructure`](@ref) を参照してください。
