```
abstract type SyntaxTree <: AbstractSyntaxStructure end
```

Abstract type for [syntax trees](https://en.wikipedia.org/wiki/Abstract_syntax_tree); that is, syntax leaves (see `SyntaxLeaf`, such as `Truth` values and `Atom`s), and their composition via `Connective`s (i.e., `SyntaxBranch`).

!!! note
    Note that `SyntaxTree`s are *ranked trees*, and (should) adhere to the `AbstractTrees` interface.


See also [`SyntaxLeaf`](@ref), [`SyntaxBranch`](@ref), [`AbstractSyntaxStructure`](@ref), [`Formula`](@ref).
