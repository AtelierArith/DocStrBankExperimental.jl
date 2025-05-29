```
grammar2symboltable(grammar::AbstractGrammar, mod::Module=Main)
```

Returns a [`SymbolTable`](@ref) populated with a mapping from symbols in the  [`AbstractGrammar`](@ref) to symbols in module `mod` or `Main`, if defined.
