```
objective_cache_factory(M::AbstractManifold, o::AbstractManifoldObjective, cache::Symbol)
```

`AbstractManifold M`上の[`AbstractManifoldObjective`](@ref) `o`のキャッシュされたバリアントを、シンボル`cache`に基づいて生成します。

以下のキャッシュが利用可能です

  * `:Simple`は[`SimpleManifoldCachedObjective`](@ref)を生成します
  * `:LRU`は[`ManifoldCachedObjective`](@ref)を生成します。この場合、`(:LRU, [:Cost, :Gradient])`の形式を使用してキャッシュする内容を指定するか、`(:LRU, [:Cost, :Gradient], 100)`を使用してキャッシュサイズを指定します。このバリアントはデフォルトで`(:LRU, [:Cost, :Gradient], 100)`となり、最大100のコストと勾配の値をキャッシュします。[^1]

[^1]: このキャッシュを使用するには、[`LRUCache.jl`](https://github.com/JuliaCollections/LRUCache.jl)をロードする必要があります。
