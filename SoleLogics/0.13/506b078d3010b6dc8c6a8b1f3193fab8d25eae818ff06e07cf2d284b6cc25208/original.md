```
abstract type SyntaxLeaf <: SyntaxStructure end
```

An atomic logical element, like a `Truth` value or an `Atom`. `SyntaxLeaf`s have `arity` equal to zero, meaning that they are not allowed to have children in tree-like syntactic structures.

# Interface

  * `syntaxstring(s::SyntaxLeaf; kwargs...)::String`
  * `dual(s::SyntaxLeaf)::SyntaxLeaf`
  * `hasdual(s::SyntaxLeaf)::Bool`

See also [`SyntaxStructure`](@ref),  [`arity`](@ref), [`SyntaxBranch`](@ref).
