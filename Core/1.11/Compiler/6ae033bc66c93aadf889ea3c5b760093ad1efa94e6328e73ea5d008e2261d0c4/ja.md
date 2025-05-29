```
matching_cache_argtypes(𝕃::AbstractLattice, linfo::MethodInstance, argtypes::SimpleArgtypes)
```

一般的な拡張格子情報を持つ `argtypes` の実装です。これはデバッグやテスト、または外部の `AbstractInterpreter` の使用のために使用されることを意図しています。一般的に `matching_cache_argtypes(::MethodInstance, ::ConditionalArgtypes)` の方が好まれ、`Conditional` 情報を転送できます。
