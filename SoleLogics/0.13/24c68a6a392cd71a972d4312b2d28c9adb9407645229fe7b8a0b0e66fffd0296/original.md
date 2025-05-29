```
tokens(φ::Formula)::AbstractVector{<:SyntaxToken}
atoms(φ::Formula)::AbstractVector{<:Atom}
truths(φ::Formula)::AbstractVector{<:Truth}
leaves(φ::Formula)::AbstractVector{<:SyntaxLeaf}
connectives(φ::Formula)::AbstractVector{<:Connective}
operators(φ::Formula)::AbstractVector{<:Operator}
ntokens(φ::Formula)::Integer
natoms(φ::Formula)::Integer
ntruths(φ::Formula)::Integer
nleaves(φ::Formula)::Integer
nconnectives(φ::Formula)::Integer
noperators(φ::Formula)::Integer
```

Return the list/number of (non-unique) `SyntaxToken`s, `Atom`s, etc... appearing in a formula.

See also [`Formula`](@ref), [`SyntaxToken`](@ref).
