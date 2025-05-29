```
objective_cache_factory(M::AbstractManifold, o::AbstractManifoldObjective, cache::Symbol)
```

[`AbstractManifoldObjective`](@ref) `o` のキャッシュされたバリアントを、シンボル `cache` に基づいて `AbstractManifold M` 上に生成します。

以下のキャッシュが利用可能です

  * `:Simple` は [`SimpleManifoldCachedObjective`](@ref) を生成します
  * `:LRU` は [`ManifoldCachedObjective`](@ref) を生成します。この場合、キャッシュするものを指定するには `(:LRU, [:Cost, :Gradient])` の形式を使用するか、キャッシュサイズを指定するには `(:LRU, [:Cost, :Gradient], 100)` を使用します。このバリアントはデフォルトで `(:LRU, [:Cost, :Gradient], 100)` となり、最大100のコストと勾配の値をキャッシュします。[^1]

[^1]: このキャッシュを使用するには [`LRUCache.jl`](https://github.com/JuliaCollections/LRUCache.jl) をロードする必要があります。
