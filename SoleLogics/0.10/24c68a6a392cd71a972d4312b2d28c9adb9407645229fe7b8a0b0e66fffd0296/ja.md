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

数式に現れる（非一意の）`SyntaxToken`、`Atom` などのリスト/数を返します。

[`Formula`](@ref) や [`SyntaxToken`](@ref) も参照してください。
