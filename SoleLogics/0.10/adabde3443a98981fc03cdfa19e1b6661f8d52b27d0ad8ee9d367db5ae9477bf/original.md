```
inlinedisplay(i::AbstractAssignment)
```

Provides a string representation of an assignment.

# Examples

```julia-repl
julia> SoleLogics.inlinedisplay(TruthDict(["a" => true, "b" => false, "c" => true]))
"TruthDict([c => ⊤, b => ⊥, a => ⊤])"

julia> SoleLogics.inlinedisplay(TruthDict(1:4, false))
"TruthDict([4 => ⊥, 2 => ⊥, 3 => ⊥, 1 => ⊥])"
```

See also [`AbstractAssignment`](@ref), [`TruthDict`](@ref).
