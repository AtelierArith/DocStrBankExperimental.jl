```
read_csg(grammarpath::AbstractString, constraintspath::OptionalPath=nothing)::ContextSensitiveGrammar
```

`grammarpath` と `constraintspath` のファイルから [`ContextSensitiveGrammar`](@ref) を読み込みます。

!!! danger
    信頼できる文法のみを開いてください。文法の一部は Julia の `eval` 関数に渡すことができます。

