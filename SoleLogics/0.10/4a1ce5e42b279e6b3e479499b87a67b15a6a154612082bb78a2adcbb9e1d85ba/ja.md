```
struct SyntaxBranch <: AbstractSyntaxBranch
    token::Connective
    children::NTuple{N,SyntaxTree} where {N}
end
```

構文ブランチのシンプルな実装。実装は*アリティ準拠*であり、構築時にトークンのアリティが提供された子の数と照合されます。

# 例

```julia-repl
julia> p,q = Atom.([p, q])
2-element Vector{Atom{String}}:
 Atom{String}: p
 Atom{String}: q

julia> branch = SyntaxBranch(CONJUNCTION, p, q)
SyntaxBranch: p ∧ q

julia> token(branch)
∧

julia> syntaxstring.(children(branch))
(p, q)

julia> ntokens(a) == nconnectives(a) + nleaves(a)
true

julia> arity(a)
2

julia> height(a)
1
```

他にも [`token`](@ref), [`children`](@ref), [`arity`](@ref), [`Connective`](@ref), [`height`](@ref), [`atoms`](@ref), [`natoms`](@ref), [`operators`](@ref), [`noperators`](@ref), [`tokens`](@ref), [`ntokens`](@ref) を参照してください。
