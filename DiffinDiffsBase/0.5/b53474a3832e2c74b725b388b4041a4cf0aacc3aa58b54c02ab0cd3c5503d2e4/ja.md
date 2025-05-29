```
termset([itr])
termset(ts::Union{Int, Symbol, AbstractTerm}...)
```

コレクションから[`TermSet`](@ref)を構築します。反復可能なコレクションを渡す代わりに、引数として直接用語を渡すことができます。この場合、`Int`または`Symbol`は`Term`に変換されます。
