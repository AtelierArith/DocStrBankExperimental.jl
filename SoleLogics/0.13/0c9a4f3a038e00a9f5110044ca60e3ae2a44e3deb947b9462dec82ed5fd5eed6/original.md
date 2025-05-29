```
abstract type AbstractAtom <: SyntaxLeaf end
```

An atom, sometimes called an atomic proposition, propositional letter (or simply *letter*), representing a fact which truth can be assessed on a logical interpretation.

Atoms are nullary tokens (i.e, they are at the leaves of a syntax tree); note that their atoms cannot be `Atom`s.

# Interface

  * `syntaxstring(s::AbstractAtom; kwargs...)::String`
  * `dual(s::AbstractAtom)::AbstractAtom`
  * `hasdual(s::AbstractAtom)::Bool`

See also [`AbstractInterpretation`](@ref), [`atoms`](@ref), [`check`](@ref), [`SyntaxToken`](@ref).
