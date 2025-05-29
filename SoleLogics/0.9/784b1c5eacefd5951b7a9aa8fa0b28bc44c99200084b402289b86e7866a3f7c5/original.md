```
abstract type SyntaxLeaf <: AbstractSyntaxStructure end
```

An atomic logical element, like a `Truth` value or an `Atom`. `SyntaxLeaf`s have `arity` equal to zero, meaning that they are not allowed to have children in tree-like syntactic structures.

See also [`AbstractSyntaxStructure`](@ref),  [`arity`](@ref), [`SyntaxBranch`](@ref).
