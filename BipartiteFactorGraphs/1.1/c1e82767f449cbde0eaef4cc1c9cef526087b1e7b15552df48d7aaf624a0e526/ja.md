```
BipartiteFactorGraph
```

変数、因子、およびエッジのデータを格納する型安定な二部無向因子グラフの実装です。ユーザーは二部構造を維持する責任があります。

グラフが構築された後、ユーザーは `Graphs.is_bipartite(graph.graph)` を使用して、グラフが実際に二部であるかどうかを確認できます。基盤となるグラフが二部でない場合、特定の関数が正しく動作せず、予期しない結果を生じる可能性があります。

# フィールド

  * `graph`: 基盤となるグラフ構造
  * `variable_data`: 変数ノードのデータの辞書で、キーは `Int` 型の要素、値は `TVar` 型です
  * `factor_data`: 因子ノードのデータの辞書で、キーは `Int` 型の要素、値は `TFac` 型です
  * `edge_data`: 変数と因子の間のエッジのデータの辞書で、キーは `UnorderedPair` 型の要素、値は `E` 型です

!!! note
    エッジデータのキーは重複エントリやアクセスエラーを避けるために `UnorderedPair` として保存されます。これは、`get_edge_data(g, v1, v2)` が `get_edge_data(g, v2, v1)` と等価であることを意味します。これにより、グラフは無向であることも示唆されます。


指定された変数、因子、およびエッジデータ型を持つ空の BipartiteFactorGraph を構築するには、次のコンストラクタを使用します。

```julia
BipartiteFactorGraph(::Type{TVar}, ::Type{TFac}, ::Type{E}, dict_type::Type{D}=Dict) where {TVar,TFac,E,D}
```

# 引数

  * `TVar`: 変数データの型
  * `TFac`: 因子データの型
  * `E`: エッジデータの型
  * `dict_type`: 変数、因子、およびエッジデータを格納するために使用される辞書の型（デフォルトは Base.Dict）

コンストラクタの代わりに、`BipartiteFactorGraph()` を `BipartiteFactorGraph(Any, Any, Any, Dict)` のエイリアスとして使用できます。

# 例

```jldoctest
julia> g = BipartiteFactorGraph(Int, Float64, String, Dict)
BipartiteFactorGraph{Int64, Float64, String} with 0 variables, 0 factors, and 0 edges

julia> add_variable!(g, 1);

julia> add_factor!(g, 2.0);

julia> add_edge!(g, 1, 2, "Hello");

julia> g
BipartiteFactorGraph{Int64, Float64, String} with 1 variables, 1 factors, and 1 edges
```
