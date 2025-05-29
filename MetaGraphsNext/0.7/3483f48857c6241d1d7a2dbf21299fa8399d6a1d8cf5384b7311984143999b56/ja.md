```
MetaGraph{
    Code<:Integer,
    Graph<:AbstractGraph{Code},
    Label,
    VertexData,
    EdgeData,
    GraphData,
    WeightFunction,
    Weight
} <: AbstractGraph{Code}
```

カスタム頂点ラベルを持つグラフタイプで、頂点、エッジ、およびグラフレベルのメタデータを含みます。

頂点ラベルは `Label` 型であり、頂点（およびエッジ、グラフ）のメタデータはそれぞれ `VertexData`（および `EdgeData`、および `GraphData`）型です。グラフが進化するにつれて変わらない頂点ラベルと、`Code<:Integer` 型であり、グラフが進化するにつれて変わる可能性のある頂点コードとの混乱を避けるために、`Label` を整数型に設定しないことをお勧めします。

# フィールド

  * `graph::Graph`: 頂点コードが `Code` 型の基礎となるデータなしのグラフ
  * `vertex_labels::Dict{Code,Label}`: 頂点コードを頂点ラベルにマッピングする辞書
  * `vertex_properties::Dict{Label,Tuple{Code,VertexData}}`: 頂点ラベルを頂点コードとメタデータにマッピングする辞書
  * `edge_data::Dict{Tuple{Label,Label},EdgeData}`: エッジラベル（例: `(label_u, label_v)`）をエッジメタデータにマッピングする辞書
  * `graph_data::GraphData`: グラフオブジェクト全体のメタデータ
  * `weight_function::WeightFunction`: エッジメタデータからエッジの重みを計算する関数、その出力は `default_weight` と同じ型でなければなりません
  * `default_weight::Weight`: エッジが存在しない場合に使用されるデフォルトの重み
