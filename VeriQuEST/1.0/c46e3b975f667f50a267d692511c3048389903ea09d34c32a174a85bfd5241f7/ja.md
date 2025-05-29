```
set_vertex_type!(::TestRound, resource, mg)
```

この関数は、リソースグラフのテストラウンドからのランダムな色パターンに基づいて、MetaGraph内の頂点タイププロパティを設定します。色パターンに従って、`DummyQubit`および`TrapQubit`タイプを頂点に割り当てます。

# 引数

  * `test_round::TestRound`: TestRoundオブジェクト。
  * `resource`: グラフとその色付けを含むリソース。
  * `mg`: 頂点タイププロパティが追加されるMetaGraph。

# 例

```julia
test_round = TestRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_vertex_type!(test_round, resource, mg)
```
