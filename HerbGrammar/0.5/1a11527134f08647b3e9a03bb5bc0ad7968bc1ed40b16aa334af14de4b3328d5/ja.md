```
read_pcsg(grammarpath::AbstractString, constraintspath::OptionalPath=nothing)::ContextSensitiveGrammar
```

指定された `grammarpath` と `constraintspath` のファイルから確率的 [`ContextSensitiveGrammar`](@ref) を読み込みます。

!!! danger
    信頼できる文法のみを開いてください。文法の一部は Julia の `eval` 関数に渡される可能性があります。

