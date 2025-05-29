```
concretize_type(::Type{ECPoint{P}}, order::Integer, cofactor::Integer; name=nothing) where P <: AbstractPoint
```

指定された順序とコファクタを持つ具体的な点タイプ `P <: AbstractPoint` の `ECPoint` を構築します。名前は、`@ECPoint{name}` 表示セマンティクスを使用してグループパラメータのエイリアスに使用されます。
