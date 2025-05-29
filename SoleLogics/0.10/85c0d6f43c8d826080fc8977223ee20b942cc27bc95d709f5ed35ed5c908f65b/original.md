```
abstract type Formula <: Syntactical end
```

Abstract type for logical formulas. Examples of `Formula`s are `SyntaxLeaf`s (for example, `Atom`s and `Truth` values), `SyntaxStructure`s (for example, `SyntaxTree`s and `LeftmostLinearForm`s) and `TruthTable`s ( enriched representation, which associates a syntactic structure with additional [memoization](https://en.wikipedia.org/wiki/Memoization) structures, which can save computational time upon [model checking](https://en.wikipedia.org/wiki/Model_checking)).

Any formula can be converted into its [`SyntaxTree`](@ref) representation via [`tree`](@ref); its [`height`](@ref) can be computed, and it can be queried for its syntax [`tokens`](@ref), [`atoms`](@ref), etc... It can be parsed from its [`syntaxstring`](@ref) representation via [`parseformula`](@ref).

# Interface

  * `tree(φ::Formula)::SyntaxTree`
  * `composeformulas(c::Connective, φs::NTuple{N,F})::F where {N,F<:Formula}`
  * See also [`Syntactical`](@ref)

# Utility functions (requiring a walk of the tree)

  * `Base.in(tok::SyntaxToken, φ::Formula)::Bool`
  * `height(φ::Formula)::Int`
  * `tokens(φ::Formula)::AbstractVector{<:SyntaxToken}`
  * `atoms(φ::Formula)::AbstractVector{<:AbstractAtom}`
  * `truths(φ::Formula)::AbstractVector{<:Truth}`
  * `leaves(φ::Formula)::AbstractVector{<:SyntaxLeaf}`
  * `connectives(φ::Formula)::AbstractVector{<:Connective}`
  * `operators(φ::Formula)::AbstractVector{<:Operator}`
  * `ntokens(φ::Formula)::Int`
  * `natoms(φ::Formula)::Int`
  * `ntruths(φ::Formula)::Int`
  * `nleaves(φ::Formula)::Int`
  * `nconnectives(φ::Formula)::Int`
  * `noperators(φ::Formula)::Int`

See also [`tree`](@ref), [`SyntaxStructure`](@ref), [`SyntaxLeaf`](@ref).
