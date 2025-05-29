```
decorate_objective!(M, o::AbstractManifoldObjective)
```

特定のデコレーターで[`AbstractManifoldObjective`](@ref)`o`を装飾します。

# オプション引数

オプション引数はデコレーターに関する必要な詳細を提供します。特定のものは、特定のデコレーターを有効にするために使用されます。

  * `cache`:           (`missing`) キャッシュを指定します。現在、`：Simple`がサポートされており、[`LRUCache.jl`](https://github.com/JuliaCollections/LRUCache.jl)をロードすると`：LRU`が使用できます。この場合、何をキャッシュし、いくつキャッシュするかを指定するタプルを提供する必要があります。例えば、`(:LRU, [:Cost, :Gradient], 10)`は、最後に使用された10回のコスト関数評価と勾配評価を保存することを示します。詳細については[`objective_cache_factory`](@ref)を参照してください。
  * `count`:           (`missing`) 呼び出される目的の呼び出しを指定します。完全なリストについては[`ManifoldCountObjective`](@ref)を参照してください。
  * `objective_type`:  (`:Riemannian`) 目的が`:Riemannian`または`:Euclidean`であることを指定します。`:Euclidean`シンボルは、最終的には両方が埋め込みからリーマン的なものに目的を変換することを指すため、`:Embedded`として指定することと同等です。

# 参照

[`objective_cache_factory`](@ref)
