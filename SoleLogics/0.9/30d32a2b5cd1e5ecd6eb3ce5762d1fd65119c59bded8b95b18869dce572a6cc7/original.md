```
struct SyntaxBranch <: SyntaxTree
    token::Connective
    children::NTuple{N,SyntaxTree} where {N}
end
```

An internal node of a syntax tree encoding a logical formula. Such a node holds a syntax `token` (a `Connective`, and has as many children as the `arity` of the token.

This implementation is *arity-compliant*, in that, upon construction, the arity of the token is checked against the number of children provided.

# Examples

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

See also [`token`](@ref), [`children`](@ref), [`arity`](@ref), [`Connective`](@ref), [`height`](@ref), [`atoms`](@ref), [`natoms`](@ref), [`operators`](@ref), [`noperators`](@ref), [`tokens`](@ref), [`ntokens`](@ref),
