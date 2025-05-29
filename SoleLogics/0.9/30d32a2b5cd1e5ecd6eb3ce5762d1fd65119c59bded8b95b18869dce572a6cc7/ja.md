```
struct SyntaxBranch <: SyntaxTree
    token::Connective
    children::NTuple{N,SyntaxTree} where {N}
end
```

論理式をエンコードする構文木の内部ノード。 このノードは構文 `token`（`Connective`）を保持し、トークンの `arity` と同じ数の子を持ちます。

この実装は *arity-compliant* であり、構築時にトークンのアリティが提供された子の数と照合されます。

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

他の情報は [`token`](@ref), [`children`](@ref), [`arity`](@ref), [`Connective`](@ref), [`height`](@ref), [`atoms`](@ref), [`natoms`](@ref), [`operators`](@ref), [`noperators`](@ref), [`tokens`](@ref), [`ntokens`](@ref) を参照してください。
