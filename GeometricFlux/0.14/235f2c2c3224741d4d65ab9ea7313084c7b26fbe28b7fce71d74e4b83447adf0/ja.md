```
GraphParallel(; node_layer=identity, edge_layer=identity, global_layer=identity,
                positional_layer=identity)
```

`FeaturedGraph`に特徴を並行して渡します。`FeaturedGraph`を入力として受け取り、特定の（ノード、エッジ、グローバル）特徴のためにレイヤーを割り当てることで指定できます。

# 引数

  * `node_layer`: ノード特徴を渡すための通常のFluxレイヤー。
  * `edge_layer`: エッジ特徴を渡すための通常のFluxレイヤー。
  * `global_layer`: グローバル特徴を渡すための通常のFluxレイヤー。
  * `positional_layer`: 位置特徴を渡すための通常のFluxレイヤー。

# 例

```jldoctest
julia> using Flux, GeometricFlux

julia> l = GraphParallel(
            node_layer=Dropout(0.5),
            global_layer=Dense(10, 5)
       )
GraphParallel(node_layer=Dropout(0.5), edge_layer=identity, global_layer=Dense(10 => 5), positional_layer=identity)
```
