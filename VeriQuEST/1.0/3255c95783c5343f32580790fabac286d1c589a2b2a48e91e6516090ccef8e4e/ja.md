```
set_vertex_type!(::Union{MBQC,ComputationRound}, resource, mg)
```

この関数は、リソースグラフ内の計算ラウンドの色パターンに基づいて、MetaGraph内の頂点タイププロパティを設定します。色パターンに従って、頂点に`ComputationQubit`タイプを割り当てます。

# 引数

  * `mbqc::Union{MBQC,ComputationRound}`: MBQCまたはComputationRoundオブジェクト。
  * `resource`: グラフとその色付けを含むリソース。
  * `mg`: 頂点タイププロパティが追加されるMetaGraph。

# 例

```julia
mbqc = MBQC()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_vertex_type!(mbqc, resource, mg)
```
