グラフホモモルフィズムをGraphvizを使用して視覚化します。

2つのグラフ（`AbstractGraph`のインスタンス）間のホモモルフィズム（`ACSetTransformation`）を視覚化します。デフォルトでは、定義域と値域はサブグラフとして描画され、頂点のマッピングは点線のエッジを使用して描画されますが、エッジマップは抑制されます。頂点とエッジのマッピングは、`node_colors`および`edge_colors`キーワード引数を介して色を使用して表示することもできます。

# 引数

  * `draw_codom=true`: 値域グラフを描画するかどうか
  * `draw_mapping=true`: エッジを使用して頂点マッピングを描画するかどうか
  * `prog="dot"`: 使用するGraphvizプログラム
  * `graph_attrs`: グラフレベルのGraphviz属性
  * `node_attrs`: ノードレベルのGraphviz属性
  * `edge_attrs`: エッジレベルのGraphviz属性
  * `node_labels=false`: ノードラベルを描画するかどうか、どの頂点属性を使用するか
  * `edge_labels=false`: エッジラベルを描画するかどうか、どのエッジ属性を使用するか
  * `node_colors=!draw_codom`: 頂点マップに基づいてノードを色付けするかどうか
  * `edge_colors=!draw_codom`: エッジマップに基づいてエッジを色付けするかどうか
