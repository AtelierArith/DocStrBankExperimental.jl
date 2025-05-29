```
identifiers([T], g, dims...; method=orthogonal_random_features)
```

ノード識別子とエッジ識別子を返します。

# 引数

  * `T`: 返されるオブジェクトの要素タイプ。
  * `g`: グラフトポロジーを表すデータ。可能なタイプは

      * 隣接行列。
      * 隣接リスト。
      * Graphsのグラフ、すなわち`SimpleGraph`、`SimpleDiGraph`、またはSimpleWeightedGraphsの`SimpleWeightedGraph`、`SimpleWeightedDiGraph`。
      * `AbstractFeaturedGraph`オブジェクト。
  * `dims`: 最初の2次元の後に続く追加の次元。
  * `method`: 利用可能なメソッドは`GraphSignals.orthogonal_random_features`と`GraphSignals.laplacian_matrix`です。

# 使用法

```jldoctest
julia> using GraphSignals

julia> V, E = 4, 5
(4, 5)

julia> batch_size = 10
10

julia> adjm = [0 1 1 1;
               1 0 1 0;
               1 1 0 1;
               1 0 1 0];

julia> node_id, edge_token = identifiers(adjm, batch_size);

julia> size(node_id)
(8, 4, 10)

julia> size(edge_id)
(8, 10, 10)
```

ノード識別子のみを生成するには[`node_identifier`](@ref)も参照してください。
