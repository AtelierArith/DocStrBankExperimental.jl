```
abstract type SyntaxTree <: SyntaxStructure end
```

Abstract type for [syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree); that is, syntax leaves (see `SyntaxLeaf`, such as `Truth` values and `Atom`s), and their composition via `Connective`s (i.e., `SyntaxBranch`).

Note that `SyntaxTree` are *ranked trees*, and (should) implement `AbstractTrees` interface.

# Interface

  * `children(φ::SyntaxTree)::NTuple{N,SyntaxTree} where N`
  * `token(φ::SyntaxTree)::Connective`
  * See also [`SyntaxStructure`](@ref)

# Utility functions

  * `tokentype(φ::SyntaxTree)`
  * `arity(φ::SyntaxTree)::Int`

# Other utility functions (requiring a walk of the tree)

  * `Base.in(tok::SyntaxToken, φ::SyntaxTree)::Bool`
  * `height(φ::SyntaxTree)::Int`
  * `tokens(φ::SyntaxTree)::AbstractVector{<:SyntaxToken}`
  * `atoms(φ::SyntaxTree)::AbstractVector{<:AbstractAtom}`
  * `truths(φ::SyntaxTree)::AbstractVector{<:Truth}`
  * `leaves(φ::SyntaxTree)::AbstractVector{<:SyntaxLeaf}`
  * `connectives(φ::SyntaxTree)::AbstractVector{<:Connective}`
  * `operators(φ::SyntaxTree)::AbstractVector{<:Operator}`
  * `ntokens(φ::SyntaxTree)::Int`
  * `natoms(φ::SyntaxTree)::Int`
  * `ntruths(φ::SyntaxTree)::Int`
  * `nleaves(φ::SyntaxTree)::Int`
  * `nconnectives(φ::SyntaxTree)::Int`
  * `noperators(φ::SyntaxTree)::Int`
  * `tokenstype(φ::SyntaxTree)`
  * `atomstype(φ::SyntaxTree)`
  * `truthstype(φ::SyntaxTree)`
  * `leavestype(φ::SyntaxTree)`
  * `connectivestype(φ::SyntaxTree)`
  * `operatorstype(φ::SyntaxTree)`
  * `composeformulas(c::Connective, φs::NTuple{N,SyntaxTree})`

See also [`SyntaxLeaf`](@ref), [`SyntaxBranch`](@ref), [`SyntaxStructure`](@ref), [`Formula`](@ref).
