```
cache_nodes!(node; scale=nothing, symbol=nothing, link=nothing, filter_fun=nothing, overwrite=false)
```

フィルターに基づいてmtgのノードをキャッシュします。これは、[`traverse!`](@ref)または[`transform!`](@ref)を使用してトラバースする際に自動的に使用されます。

# 例

```julia
file = joinpath(dirname(dirname(pathof(MultiScaleTreeGraph))), "test", "files", "simple_plant.mtg")
mtg = read_mtg(file, Dict)

# すべての葉ノードをキャッシュします:
cache_nodes!(mtg, symbol="Leaf")

# キャッシュされたノードはmtgのtraversal_cacheフィールドに格納されます（ここでは、2つの葉）:
@test MultiScaleTreeGraph.node_traversal_cache(mtg)["_cache_c0bffb8cc8a9b075e40d26be9c2cac6349f2a790"] == [get_node(mtg, 5), get_node(mtg, 7)]

# その後、トラバースでキャッシュされたノードを使用できます:
traverse(mtg, x -> symbol(x), symbol="Leaf") == ["Leaf", "Leaf"]
```
