```
grammar2symboltable(grammar::AbstractGrammar, mod::Module=Main)
```

[`AbstractGrammar`](@ref) のシンボルからモジュール `mod` または定義されている場合は `Main` のシンボルへのマッピングで populated された [`SymbolTable`](@ref) を返します。
