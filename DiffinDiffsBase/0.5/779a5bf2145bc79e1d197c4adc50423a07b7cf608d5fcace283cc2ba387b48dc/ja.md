```
TermSet([itr])
TermSet(ts::Union{Int, Symbol, AbstractTerm}...)
```

コレクションの用語から[`TermSet`](@ref)を構築します。反復可能なコレクションを渡す代わりに、用語を引数として直接渡すことができます。この場合、`Int`または`Symbol`は`Term`に変換されます。コンストラクタのエイリアスである[`termset`](@ref)も参照してください。
