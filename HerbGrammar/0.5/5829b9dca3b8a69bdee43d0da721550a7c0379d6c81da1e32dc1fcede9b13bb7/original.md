```
store_csg(g::ContextSensitiveGrammar, grammarpath::AbstractString, constraintspath::OptionalPath=nothing)
```

Writes a [`ContextSensitiveGrammar`](@ref) to the files at `grammarpath` and `constraintspath`. The `grammarpath` file will contain a [`ContextSensitiveGrammar`](@ref) definition, and the `constraintspath` file will contain the [`AbstractConstraint`](@ref)s of the [`ContextSensitiveGrammar`](@ref).
