```
arity(φ::SyntaxTree)::Integer
arity(tok::Connective)::Integer
```

Return the `arity` of a `Connective` or a `SyntaxTree`. The `arity` is an integer representing the number of allowed children for a node in a tree. `Connective`s with `arity` equal to 0, 1 or 2 are called `nullary`, `unary` and `binary`, respectively. `SyntaxLeaf`s (`Atom`s and `Truth` values) are always nullary.

See also [`SyntaxLeaf`](@ref), [`Connective`](@ref), [`SyntaxBranch`](@ref).
