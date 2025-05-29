```
objective_cache_factory(M::AbstractManifold, o::AbstractManifoldObjective, cache::Tuple{Symbol, Array, Array})
objective_cache_factory(M::AbstractManifold, o::AbstractManifoldObjective, cache::Tuple{Symbol, Array})
```

[`AbstractManifoldObjective`](@ref) `o` のキャッシュされたバリアントを、シンボル `cache[1]` に基づいて `AbstractManifold M` 上で生成します。第二要素 `cache[2]` はキャッシュへのさらなる引数であり、オプションの第三要素はキーワード引数として渡されます。

利用可能なすべてのキャッシュについては、シンボルを使用したよりシンプルなバリアントを参照してください。
