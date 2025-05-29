```
interpret(a::AbstractAtom, i::AbstractAssignment, args...; kwargs...)::SyntaxLeaf
```

Return the value corresponding to the [`Atom`](@ref) contained in the  [`AbstractAssignment`](@ref). When interpreting a single atom, if the lookup fails,  then return the atom itself.

# Examples

```julia-repl
julia>interpret(Atom("a"), TruthDict(["a" => true, "b" => false, "c" => true]))
⊤

julia>interpret(Atom(3), TruthDict(1:4, false))
⊥
```

See also [`AbstractAssignment`](@ref), [`Atom`](@ref),  [`DefaultedTruthDict`](@ref), [`TruthDict`](@ref).
