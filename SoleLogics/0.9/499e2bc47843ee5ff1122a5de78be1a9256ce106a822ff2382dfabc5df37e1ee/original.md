```
struct Atom{V} <: SyntaxLeaf
    value::V
end
```

An atom, sometimes called an atomic proposition, propositional letter (or simply *letter*), of type `Atom{V}` wraps a `value::V` representing a fact which truth can be assessed on a logical interpretation.

Atoms are nullary tokens (i.e, they are at the leaves of a syntax tree); note that their atoms cannot be `Atom`s.

See also [`AbstractInterpretation`](@ref), [`atoms`](@ref), [`check`](@ref), [`SyntaxToken`](@ref).
