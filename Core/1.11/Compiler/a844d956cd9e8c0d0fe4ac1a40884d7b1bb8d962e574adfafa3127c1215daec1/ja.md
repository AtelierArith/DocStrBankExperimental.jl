```
matching_cache_argtypes(𝕃::AbstractLattice, linfo::MethodInstance) ->
    (cache_argtypes::Vector{Any}, overridden_by_const::BitVector)
```

引数の型 `cache_argtypes::Vector{Any}` を `linfo` に対して返します。これはネイティブなJulia型ドメインにあります。`overridden_by_const::BitVector` はすべて `false` であり、追加の拡張格情報は存在しないことを意味します。

```
matching_cache_argtypes(𝕃::AbstractLattice, linfo::MethodInstance, argtypes::ForwardableArgtypes) ->
    (cache_argtypes::Vector{Any}, overridden_by_const::BitVector)
```

いくつかの `argtypes` に対して `linfo` のためのキャッシュ正しい拡張格引数型 `cache_argtypes::Vector{Any}` を返します。これは、どの引数が追加の拡張格情報を含むかを示す `overridden_by_const::BitVector` に伴います。

理論的には、提供された `linfo` と `given_argtypes` に対して一致する `InferenceResult` を含む `cache` が存在する可能性があります。この関数の目的は、`cache_lookup(𝕃, linfo, argtypes, cache).argtypes` に対して有効な値を返すことです。これにより、最初にキャッシュ正しい `InferenceResult` を構築できるようになります。
