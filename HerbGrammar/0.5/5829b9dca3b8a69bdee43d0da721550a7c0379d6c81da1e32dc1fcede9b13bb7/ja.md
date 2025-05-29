```
store_csg(g::ContextSensitiveGrammar, grammarpath::AbstractString, constraintspath::OptionalPath=nothing)
```

[`ContextSensitiveGrammar`](@ref) を `grammarpath` と `constraintspath` のファイルに書き込みます。`grammarpath` ファイルには [`ContextSensitiveGrammar`](@ref) の定義が含まれ、`constraintspath` ファイルには [`ContextSensitiveGrammar`](@ref) の [`AbstractConstraint`](@ref) が含まれます。
