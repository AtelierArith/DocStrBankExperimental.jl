```
read_csg(grammarpath::AbstractString, constraintspath::OptionalPath=nothing)::ContextSensitiveGrammar
```

Reads a [`ContextSensitiveGrammar`](@ref) from the files at `grammarpath` and `constraintspath`.

!!! danger
    Only open trusted grammars.  Parts of the grammar can be passed to Julia's `eval` function.

