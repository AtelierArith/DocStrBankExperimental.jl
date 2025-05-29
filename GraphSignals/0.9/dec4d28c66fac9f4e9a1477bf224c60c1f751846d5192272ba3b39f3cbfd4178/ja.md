```
node_identifier([T], g, dims...; method=GraphSignals.orthogonal_random_features)
```

グラフ `g` のノード識別子を追加の次元 `dims` で構築します。

# 引数

  * `T`: 戻り値のオブジェクトの要素型。
  * `g`: グラフのトポロジーを表すデータ。可能な型は

      * 隣接行列。
      * 隣接リスト。
      * Graphs のグラフ、すなわち `SimpleGraph`、`SimpleDiGraph`、または SimpleWeightedGraphs の `SimpleWeightedGraph`、`SimpleWeightedDiGraph`。
      * `AbstractFeaturedGraph` オブジェクト。
  * `dims`: 最初の2つの次元の後に続く追加の次元。
  * `method`: 利用可能なメソッドは `GraphSignals.orthogonal_random_features` と `GraphSignals.laplacian_matrix` です。

# 使用法

```jldoctest
julia> using GraphSignals

julia> adjm = [0 1 1 1;
               1 0 1 0;
               1 1 0 1;
               1 0 1 0];

julia> batch_size = 10
10

julia> node_id = node_identifier(adjm, batch_size; method=GraphSignals.orthogonal_random_features);

julia> size(node_id)
(4, 4, 10)
```

ノード/エッジ識別子については [`identifiers`](@ref) を参照してください。
