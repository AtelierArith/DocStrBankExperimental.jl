```
abstract type Formula <: Syntactical end
```

Abstract type for logical formulas. Examples of `Formula`s are `SyntaxLeaf`s (for example, `Atom`s and `Truth` values), `AbstractSyntaxStructure`s (for example, `SyntaxTree`s and `LeftmostLinearForm`s) and `TruthTable`s ( enriched representation, which associates a syntactic structure with additional [memoization](https://en.wikipedia.org/wiki/Memoization) structures, which can save computational time upon [model checking](https://en.wikipedia.org/wiki/Model_checking)).

Any formula can be converted into its [`SyntaxTree`](@ref) representation via [`tree`](@ref); its [`height`](@ref) can be computed, and it can be queried for its syntax [`tokens`](@ref), [`atoms`](@ref), etc... It can be parsed from its [`syntaxstring`](@ref) representation via [`parseformula`](@ref).

See also [`tree`](@ref), [`AbstractSyntaxStructure`](@ref), [`SyntaxLeaf`](@ref).
